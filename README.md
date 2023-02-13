# Setup_selenium_chrome_on_the_windows_linux

- Setting up and running Chrome and Selenium on the CentOS 8 terminal or windows environment
- The guide is based on CentOS 8, but most of it is the same.
```
# cat /etc/redhat-release
CentOS Stream release 8

confirmed at 2023.02.13
```

## update the all packages, if necessary
```
# yum update
```

## create a new google-chrome repo
```bash
# vi /etc/yum.repos.d/google-chrome.repo

[google-chrome]
name=google-chrome
baseurl=http://dl.google.com/linux/chrome/rpm/stable/x86_64
enabled=1
gpgcheck=1
gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub
```

## Install goole-chrome
```bash
# yum install google-chrome-stable
google-chrome                                                                                                                    15 kB/s | 3.6 kB     00:00
Last metadata expiration check: 0:00:01 ago on Mon 13 Feb 2023 01:04:55 PM KST.
Dependencies resolved.
================================================================================================================================================================
 Package                                  Architecture            Version                                                  Repository                      Size
================================================================================================================================================================
Installing:
 google-chrome-stable                     x86_64                  110.0.5481.77-1                                          google-chrome                   95 M
Installing dependencies:
 adwaita-cursor-theme                     noarch                  3.28.0-3.el8                                             appstream                      647 k
 adwaita-icon-theme                       noarch                  3.28.0-3.el8                                             appstream                       11 M
 alsa-lib                                 x86_64                  1.2.8-2.el8                                              appstream                      497 k
 at-spi2-atk                              x86_64                  2.26.2-1.el8                                             appstream                       89 k
 at-spi2-core                             x86_64                  2.28.0-1.el8                                             appstream                      169 k
 atk                                      x86_64                  2.28.1-1.el8                                             appstream                      272 k
 colord-libs                              x86_64                  1.4.2-1.el8                                              appstream                      236 k
 fribidi                                  x86_64                  1.0.4-9.el8                                              appstream                       89 k
 gdk-pixbuf2-modules                      x86_64                  2.36.12-5.el8                                            appstream                      109 k
 graphite2                                x86_64                  1.3.10-10.el8                                            appstream                      122 k
 gtk-update-icon-cache                    x86_64                  3.22.30-11.el8                                           appstream                       32 k
 gtk3                                     x86_64                  3.22.30-11.el8                                           appstream                      4.5 M
 harfbuzz                                 x86_64                  1.7.5-3.el8                                              appstream                      295 k
 ..생략..
 pango                                    x86_64                  1.42.4-8.el8                                             appstream                      297 k
 rest                                     x86_64                  0.8.1-2.el8                                              appstream                       70 k
 vulkan-loader                            x86_64                  1.2.189.0-1.el8                                          appstream                      121 k
Installing weak dependencies:
 dconf                                    x86_64                  0.28.0-4.el8                                             appstream                      108 k
Enabling module streams:
 llvm-toolset                                                     rhel8

Transaction Summary
================================================================================================================================================================
Install  52 Packages

Total download size: 154 M
Installed size: 496 M
Is this ok [y/N]: y
Downloading Packages:
(1/52): alsa-lib-1.2.8-2.el8.x86_64.rpm                                                                                          11 MB/s | 497 kB     00:00
(2/52): at-spi2-atk-2.26.2-1.el8.x86_64.rpm                                                                                     5.0 MB/s |  89 kB     00:00
(3/52): adwaita-cursor-theme-3.28.0-3.el8.noarch.rpm                                                                            8.2 MB/s | 647 kB     00:00
(4/52): at-spi2-core-2.28.0-1.el8.x86_64.rpm                                                                                    7.6 MB/s | 169 kB     00:00
(5/52): colord-libs-1.4.2-1.el8.x86_64.rpm                                                                                       17 MB/s | 236 kB     00:00
(6/52): atk-2.28.1-1.el8.x86_64.rpm                                                                                             8.5 MB/s | 272 kB     00:00
(7/52): dconf-0.28.0-4.el8.x86_64.rpm                                                                                           2.9 MB/s | 108 kB     00:00
(8/52): fribidi-1.0.4-9.el8.x86_64.rpm                                                                                          2.9 MB/s |  89 kB     00:00
(9/52): gdk-pixbuf2-modules-2.36.12-5.el8.x86_64.rpm                                                                            7.7 MB/s | 109 kB     00:00
(10/52): graphite2-1.3.10-10.el8.x86_64.rpm                                                                                     5.6 MB/s | 122 kB     00:00
(11/52): gtk-update-icon-cache-3.22.30-11.el8.x86_64.rpm                                                                        2.5 MB/s |  32 kB     00:00
(12/52): harfbuzz-1.7.5-3.el8.x86_64.rpm                                                                                         16 MB/s | 295 kB     00:00
(13/52): hicolor-icon-theme-0.17-2.el8.noarch.rpm                                                                               917 kB/s |  49 kB     00:00
..생략..
(45/52): liberation-fonts-common-2.00.3-7.el8.noarch.rpm                                                                        4.0 MB/s |  25 kB     00:00
(46/52): liberation-mono-fonts-2.00.3-7.el8.noarch.rpm                                                                          4.7 MB/s | 505 kB     00:00
(47/52): liberation-sans-fonts-2.00.3-7.el8.noarch.rpm                                                                          5.3 MB/s | 610 kB     00:00
(48/52): liberation-serif-fonts-2.00.3-7.el8.noarch.rpm                                                                         3.3 MB/s | 609 kB     00:00
(49/52): libpciaccess-0.14-1.el8.x86_64.rpm                                                                                     4.1 MB/s |  32 kB     00:00
(50/52): mesa-vulkan-drivers-22.3.0-2.el8.x86_64.rpm                                                                             11 MB/s | 8.8 MB     00:00
(51/52): llvm-libs-15.0.7-1.module_el8.8.0+1258+af79b238.x86_64.rpm                                                              19 MB/s |  27 MB     00:01
(52/52): google-chrome-stable-110.0.5481.77-1.x86_64.rpm                                                                         11 MB/s |  95 MB     00:09
----------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                            14 MB/s | 154 MB     00:11
google-chrome                                                                                                                    36 kB/s |  12 kB     00:00
Importing GPG key 0x7FAC5991:
 Userid     : "Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>"
 Fingerprint: 4CCA 1EAF 950C EE4A B839 76DC A040 830F 7FAC 5991
 From       : https://dl-ssl.google.com/linux/linux_signing_key.pub
Is this ok [y/N]: y
Key imported successfully
Importing GPG key 0xD38B4796:
 Userid     : "Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>"
 Fingerprint: EB4C 1BFD 4F04 2F6D DDCC EC91 7721 F63B D38B 4796
 From       : https://dl-ssl.google.com/linux/linux_signing_key.pub
Is this ok [y/N]: y
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                                        1/1
  Installing       : libXfixes-5.0.3-7.el8.x86_64                                                                                                          1/52
  Installing       : liberation-fonts-common-1:2.00.3-7.el8.noarch                                                                                         2/52
  Installing       : libwayland-client-1.21.0-1.el8.x86_64                                                                                                 3/52
  Installing       : libjpeg-turbo-1.5.3-12.el8.x86_64                                                                                                     4/52
  Installing       : atk-2.28.1-1.el8.x86_64                                                                                                               5/52
  Installing       : libXdamage-1.1.4-14.el8.x86_64                                                                                                        6/52
  Installing       : libXrandr-1.5.2-1.el8.x86_64                                                                                                          7/52
  Installing       : libXi-1.7.10-1.el8.x86_64                                                                                                             8/52
  Installing       : libXcomposite-0.4.4-14.el8.x86_64                                                                                                     9/52
  Installing       : libXtst-1.2.3-7.el8.x86_64                                                                                                           10/52
  Installing       : at-spi2-core-2.28.0-1.el8.x86_64                                                                                                     11/52
  Running scriptlet: at-spi2-core-2.28.0-1.el8.x86_64                                                                                                     11/52
  Installing       : at-spi2-atk-2.26.2-1.el8.x86_64                                                                                                      12/52
  Running scriptlet: at-spi2-atk-2.26.2-1.el8.x86_64                                                                                                      12/52
..생략..                                                                                        46/52
  Installing       : dconf-0.28.0-4.el8.x86_64                                                                                                            47/52
  Installing       : alsa-lib-1.2.8-2.el8.x86_64                                                                                                          48/52
  Running scriptlet: alsa-lib-1.2.8-2.el8.x86_64                                                                                                          48/52
  Installing       : adwaita-cursor-theme-3.28.0-3.el8.noarch                                                                                             49/52
  Installing       : adwaita-icon-theme-3.28.0-3.el8.noarch                                                                                               50/52
  Installing       : gtk3-3.22.30-11.el8.x86_64                                                                                                           51/52
  Running scriptlet: google-chrome-stable-110.0.5481.77-1.x86_64                                                                                          52/52
  Installing       : google-chrome-stable-110.0.5481.77-1.x86_64                                                                                          52/52
  Running scriptlet: google-chrome-stable-110.0.5481.77-1.x86_64                                                                                          52/52
  Running scriptlet: dconf-0.28.0-4.el8.x86_64                                                                                                            52/52
  Running scriptlet: google-chrome-stable-110.0.5481.77-1.x86_64                                                                                          52/52
  Running scriptlet: hicolor-icon-theme-0.17-2.el8.noarch                                                                                                 52/52
  Running scriptlet: adwaita-icon-theme-3.28.0-3.el8.noarch                                                                                               52/52
  Verifying        : adwaita-cursor-theme-3.28.0-3.el8.noarch                                                                                              1/52
  Verifying        : adwaita-icon-theme-3.28.0-3.el8.noarch                                                                                                2/52
  Verifying        : alsa-lib-1.2.8-2.el8.x86_64                                                                                                           3/52
 ..생략..                                                                                    45/52
  Verifying        : liberation-fonts-1:2.00.3-7.el8.noarch                                                                                               46/52
  Verifying        : liberation-fonts-common-1:2.00.3-7.el8.noarch                                                                                        47/52
  Verifying        : liberation-mono-fonts-1:2.00.3-7.el8.noarch                                                                                          48/52
  Verifying        : liberation-sans-fonts-1:2.00.3-7.el8.noarch                                                                                          49/52
  Verifying        : liberation-serif-fonts-1:2.00.3-7.el8.noarch                                                                                         50/52
  Verifying        : libpciaccess-0.14-1.el8.x86_64                                                                                                       51/52
  Verifying        : google-chrome-stable-110.0.5481.77-1.x86_64                                                                                          52/52

Installed:
  adwaita-cursor-theme-3.28.0-3.el8.noarch          adwaita-icon-theme-3.28.0-3.el8.noarch                     alsa-lib-1.2.8-2.el8.x86_64
  at-spi2-atk-2.26.2-1.el8.x86_64                   at-spi2-core-2.28.0-1.el8.x86_64                           atk-2.28.1-1.el8.x86_64
  colord-libs-1.4.2-1.el8.x86_64                    dconf-0.28.0-4.el8.x86_64                                  fribidi-1.0.4-9.el8.x86_64
  gdk-pixbuf2-modules-2.36.12-5.el8.x86_64          google-chrome-stable-110.0.5481.77-1.x86_64                graphite2-1.3.10-10.el8.x86_64
  gtk-update-icon-cache-3.22.30-11.el8.x86_64       gtk3-3.22.30-11.el8.x86_64                                 harfbuzz-1.7.5-3.el8.x86_64
  hicolor-icon-theme-0.17-2.el8.noarch              jasper-libs-2.0.14-5.el8.x86_64                            jbigkit-libs-2.1-14.el8.x86_64
  lcms2-2.9-2.el8.x86_64                            libX11-xcb-1.6.8-5.el8.x86_64                              libXcomposite-0.4.4-14.el8.x86_64
  libXcursor-1.1.15-3.el8.x86_64                    libXdamage-1.1.4-14.el8.x86_64                             libXfixes-5.0.3-7.el8.x86_64
  libXft-2.3.3-1.el8.x86_64                         libXi-1.7.10-1.el8.x86_64                                  libXinerama-1.1.4-1.el8.x86_64
  libXrandr-1.5.2-1.el8.x86_64                      libXtst-1.2.3-7.el8.x86_64                                 libdatrie-0.2.9-7.el8.x86_64
  libdrm-2.4.114-1.el8.x86_64                       libepoxy-1.5.8-1.el8.x86_64                                liberation-fonts-1:2.00.3-7.el8.noarch
  liberation-fonts-common-1:2.00.3-7.el8.noarch     liberation-mono-fonts-1:2.00.3-7.el8.noarch                liberation-sans-fonts-1:2.00.3-7.el8.noarch
  liberation-serif-fonts-1:2.00.3-7.el8.noarch      libjpeg-turbo-1.5.3-12.el8.x86_64                          libpciaccess-0.14-1.el8.x86_64
  libthai-0.1.27-2.el8.x86_64                       libtiff-4.0.9-27.el8.x86_64                                libwayland-client-1.21.0-1.el8.x86_64
  libwayland-cursor-1.21.0-1.el8.x86_64             libwayland-egl-1.21.0-1.el8.x86_64                         libwayland-server-1.21.0-1.el8.x86_64
  libxshmfence-1.3-2.el8.x86_64                     llvm-libs-15.0.7-1.module_el8.8.0+1258+af79b238.x86_64     mesa-libgbm-22.3.0-2.el8.x86_64
  mesa-vulkan-drivers-22.3.0-2.el8.x86_64           pango-1.42.4-8.el8.x86_64                                  rest-0.8.1-2.el8.x86_64
  vulkan-loader-1.2.189.0-1.el8.x86_64

Complete!
```

## check installed chrome version
```bash
1) rpm command
# rpm -qa | grep google-chrome
google-chrome-stable-110.0.5481.77-1.x86_64

2) run google-chrome with --version
# google-chrome --version
Google Chrome 110.0.5481.77
```

## Check the Chrome driver and download it 
- You need to download it with the same version as the installed chrome
- download: https://sites.google.com/chromium.org/driver/
- find driver and get it
e.g) if the downloaded '110.0.5481.77', the chrome driver must also be '110.0.5481.77'


```bash
(test) download google-chromedriver '110.0.5481.77'
- https://chromedriver.storage.googleapis.com/index.html?path=110.0.5481.77/

# wget https://chromedriver.storage.googleapis.com/110.0.5481.77/chromedriver_linux64.zip
--2023-02-13 13:09:28--  https://chromedriver.storage.googleapis.com/110.0.5481.77/chromedriver_linux64.zip
Resolving chromedriver.storage.googleapis.com (chromedriver.storage.googleapis.com)... 142.251.42.208, 2404:6800:4004:827::2010
Connecting to chromedriver.storage.googleapis.com (chromedriver.storage.googleapis.com)|142.251.42.208|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7396711 (7.1M) [application/zip]
Saving to: ‘chromedriver_linux64.zip’

chromedriver_linux64.zip                100%[===============================================================================>]   7.05M  13.0MB/s    in 0.5s

2023-02-13 13:09:30 (13.0 MB/s) - ‘chromedriver_linux64.zip’ saved [7396711/7396711]
```

## Unzip Chrome driver and move file you want.
```
# unzip chromedriver_linux64.zip
Archive:  chromedriver_linux64.zip
  inflating: chromedriver
  inflating: LICENSE.chromedriver


# mkdir chromedrv
# ll
total 21664
-rwxr-xr-x. 1 root root 14452880 Feb  1 06:41 chromedriver
-rw-r--r--. 1 root root  7396711 Feb  8 17:07 chromedriver_linux64.zip
drwxr-xr-x. 2 root root        6 Feb 13 13:09 chromedrv
-rw-r--r--. 1 root root   326388 Feb  1 06:41 LICENSE.chromedriver
drwxr-xr-x. 6 root root     4096 Feb  3  2022 sslscan

# mv chromedriver chromedrv
# mmv chromedriver_linux64.zip chromedrv
# ll
total 7548
-rw-r--r--. 1 root root 7396711 Feb  8 17:07 chromedriver_linux64.zip
drwxr-xr-x. 2 root root      26 Feb 13 13:09 chromedrv
-rw-r--r--. 1 root root  326388 Feb  1 06:41 LICENSE.chromedriver
drwxr-xr-x. 6 root root    4096 Feb  3  2022 sslscan

# mv chromedriver_linux64.zip chromedrv
# ll
total 324
drwxr-xr-x. 2 root root     58 Feb 13 13:10 chromedrv
-rw-r--r--. 1 root root 326388 Feb  1 06:41 LICENSE.chromedriver
drwxr-xr-x. 6 root root   4096 Feb  3  2022 sslscan

# mv LICENSE.chromedriver chromedrv/
```

## O.K done, now let's do Hello_word
- Please adjust the arguments appropriately when running chrome.

### On the Linunx terminal (tested centOS 8 - SSH)

```python
# hello_world.py

import sys
from selenium import webdriver
from selenium.webdriver.chrome.options import Options

class Bcolors:
    Black = '\033[30m'
    Red = '\033[31m'
    Green = '\033[32m'
    Yellow = '\033[33m'
    Blue = '\033[34m'
    Magenta = '\033[35m'
    Cyan = '\033[36m'
    White = '\033[37m'
    Endc = '\033[0m'
    BOLD = '\033[1m'
    UNDERLINE = '\033[4m'


def chrome_webdriver_linux():
    options = Options()
    user_agent = 'Mozilla/5.0 (Macintosh; Intel Mac OS X 13_2) AppleWebKit/537.36 (KHTML, like Gecko) ' \
                 'Chrome/110.0.0.0 Safari/537.36'
    options.add_argument(f'user-agent={user_agent}')
    options.add_argument('--headless')
    options.add_argument('--window-size=1920x1080')
    options.add_argument('--disable-gpu')
    options.add_argument('--no-sandbox')

    driver = webdriver.Chrome(executable_path='/data/tools/chromedrv/chromedriver', options=options)
    return driver


def main():
    url = 'https://www.google.com'
    driver = chrome_webdriver()
    driver.get(url)
    driver.implicitly_wait(10)

    # print(driver.page_source)
    print(driver.title)
    driver.close()


if __name__ == '__main__':
    try:
        main()
    except KeyboardInterrupt:
        sys.exit(0)
    except Exception as e:
        print(f'{Bcolors.Yellow}- ::Exception:: Func:[{__name__.__name__}] Line:[{sys.exc_info()[-1].tb_lineno}] [{type(e).__name__}] {e}{Bcolors.Endc}')
```

### On the Windows (tested Windows 10 pro)
- Below i used webdriver_manager, If you want to use webdriver_manager, install the webdriver_manager package.

```python
# hello_world.py

import sys
from selenium import webdriver
from selenium.webdriver.chrome.service import Service as ChromeService
from selenium.webdriver.chrome.options import Options
from webdriver_manager.chrome import ChromeDriverManager


def chrome_webdriver_windows():
    chrome_service = ChromeService(executable_path=ChromeDriverManager().install())
    options = Options()
    user_agent = 'Mozilla/5.0 (Macintosh; Intel Mac OS X 13_2) AppleWebKit/537.36 (KHTML, like Gecko) ' \
                 'Chrome/110.0.0.0 Safari/537.36'
    options.add_argument(f'user-agent={user_agent}')
    options.add_argument('--headless')
    options.add_argument('--window-size=1920x1080')
    # options.add_experimental_option('detach', True)                           
    # options.add_experimental_option('excludeSwitches', ['enable-logging']) 

    driver = webdriver.Chrome(service=chrome_service, options=options)
    return driver


def main():
    url = 'https://www.google.com'
    driver = chrome_webdriver()
    driver.get(url)
    driver.implicitly_wait(10)

    # print(driver.page_source)
    print(driver.title)
    driver.close()


if __name__ == '__main__':
    try:
        main()
    except KeyboardInterrupt:
        sys.exit(0)
    except Exception as e:
        print(f'{Bcolors.Yellow}- ::Exception:: Func:[{__name__.__name__}] Line:[{sys.exc_info()[-1].tb_lineno}] [{type(e).__name__}] {e}{Bcolors.Endc}')
```

## Finally, the required packages are as follows
```
# cat requirements.txt

selenium
webdriver-manager  # <-- on the windows
```
