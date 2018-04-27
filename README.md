## Electrum over Tor: XVG

##### _lightweight VERGE client for connecting to the XVG Tor Electrum Server_

![Electrum-XVG](https://raw.githubusercontent.com/vergecurrency/electrum-xvg-tor/master/electrumlogo.png)

[![Build Status](https://travis-ci.org/vergecurrency/electrum-xvg-tor.svg?branch=master)](https://travis-ci.org/vergecurrency/electrum-xvg-tor)

Licence: GNU GPL v3

_Authors: Sunerok, Bitspill, Whit3water & CryptoRekt_

## Language: 
Python

## Homepage: 
https://Vergecurrency.com/

## Download TOR: 
https://www.torproject.org/download/download

## For binary windows release, just run Tor, and then run the electrum .exe

![electrum-windows](http://i.imgur.com/E4zj9JL.png)




## 1.a) Getting Started With Ubuntu/Linux:
```
sudo apt-get update
```

```
sudo apt-get install tor
```

```
sudo service tor start && sudo service tor stop
```

####  1.) Go to /etc/tor/ and edit the torrc file. _(you can use sudo nano torrc)_
```
cd /etc/tor
```

```
sudo nano torrc
```
#### 2.) Remove the # before the line that starts with SocksPort 9050: 


Before:
```
## Tor opens a SOCKS proxy on port 9050 by default -- even if you don't
## configure one below. Set "SOCKSPort 0" if you plan to run Tor only
## as a relay, and not make any local application connections yourself.
#SOCKSPort 9050 # Default: Bind to localhost:9050 for local connections.
#SOCKSPort 192.168.0.1:9100 # Bind to this address:port too.

```

After:
_(should look like this)_
```
## Tor opens a SOCKS proxy on port 9050 by default -- even if you don't
## configure one below. Set "SOCKSPort 0" if you plan to run Tor only
## as a relay, and not make any local application connections yourself.
SOCKSPort 9050 # Default: Bind to localhost:9050 for local connections.
#SOCKSPort 192.168.0.1:9100 # Bind to this address:port too.

```

#### 3.) Save torrc:
```
CTRL+X > Y > ENTER
```

#### 4.) Restart Tor:
```
sudo service tor restart
```


## Now we install the electrum wallet:

```
sudo apt-get install git pyqt4-dev-tools python-pip python-dev python-slowaes python-pip
```

```
sudo pip install pyasn1 pyasn1-modules pbkdf2 tlslite qrcode
```

```
git clone https://github.com/vergecurrency/electrum-xvg-tor && cd electrum-xvg-tor
```

```
pyrcc4 icons.qrc -o gui/qt/icons_rc.py
```

```
sudo python setup.py install
```

```
chmod +x ./electrum-xvg
```

## To run Electrum from this directory, just do:

```
./electrum-xvg
```

## To start Electrum from your web browser, see:

http://electrum-verge.xyz/Verge_URIs.html


## To update your copy of the electrum client:

```
cd electrum-xvg
```
```
git pull
```
```
sudo python setup.py install
```



## 1.b) Installing TOR Browser


#### 1.) Download the latest Tor browser from the official distribution website:

https://www.torproject.org/projects/torbrowser.html.en

#### 2.) Download the architecture-appropriate file above, save it somewhere, then run one of the following two commands to extract the package archive:

```
tar -xvJf tor-browser-linux32-7.5.3_LANG.tar.xz
```
###### or (for the 64-bit version):

```
tar -xvJf tor-browser-linux64-7.5.3_LANG.tar.xz
```
###### _(where LANG is the language listed in the filename)._

#### 3.) Once that's done, switch to the Tor browser directory by running:

```	
cd tor-browser_LANG
```
#### 4.) To run Tor Browser, click either on the Tor Browser or the Tor Browser Setup icon or execute the start-tor-browser.desktop file in a terminal:

```
./start-tor-browser.desktop
```

###### Note: Before you can use Tor browser you need to configure the Tor network settings. If you currently reside in a country that does not have connection limitations on Tor, Simply press connect and Tor browser will automatically configure itself.

---------------------------------------------
###### _Tor Browser is required to be open and running in the background in order for the electrum tor wallet to connect._
---------------------------------------------



## 1.c) TOR Browser Setup Instructions For Countries With Restrictions: 


#### If Tor is blocked in your country:

##### 1.) Click the Configure button to use a bridge or proxy to connect to Tor.

##### 2.) In the next window, Select Yes.

##### 3.) Next, select the default obfs4 bridge.

##### 4.) The next window asks you if you need to use a local proxy to access the Internet. Normally you can connect the Tor network via Tor bridge so just select No.

After that, the Tor browser will try to establish a connection to the Tor network.

###### _If the connection failed, then go back to the previous step and configure a proxy to access the Internet. See 1.d below_



## 1.d) Setup Instructions for ShadowSocks

#### Debian/Ubuntu
```
sudo apt-get update
```
```
sudo apt-get install python-pip 
```
```
sudo apt-get install python-setuptools m2crypto
```
```
sudo pip install shadowsocks
```
#### CentOS/RHEL
```
sudo yum install m2crypto python-setuptools
```
```
sudo easy_install pip
```
```
sudo pip install shadowsocks
```
#### Create a configuration file:
```
sudo nano /etc/shadowsocks.json
```
#### Put the following text into the file:
```
{
"server":"your_server_ip",
"server_port":8000,
"local_port":1080,
"password":"your_passwd",
"timeout":600,
"method":"aes-256-cfb"
}
```
#### Explanation of each field:
```
server:  your hostname or server IP (IPv4/IPv6).
server_port:  server port number.
local_port:  local port number.
password:  a password used to encrypt transfer.
timeout:  connections timeout in seconds.
method:  encryption method, “bf-cfb”, “aes-256-cfb”, “des-cfb”, “rc4”, etc. Default is table, which is not secure. “aes-256-cfb” is recommended.
```

#### To save:

CTRL+X > Y > ENTER

#### Start shadowsocks server:
```
sudo ssserver -c /etc/shadowsocks.json -d start
```
#### To stop shadowsocks server:
```
sudo ssserver -d stop
```
#### Restart Shadowsocks server:
```
sudo ssserver -c /etc/shadowsocks.json -d restart
```
#### Check Shadowsocks log
```
less /var/log/shadowsocks.log
```
#### Automatically start shadowsocks service
```
sudo nano /etc/rc.local
```
#### Add the following lines above exit 0 line in rc.local:

#### Automatically start shadowsocks client
```
/usr/bin/python /usr/bin/sslocal -c /etc/shadowsocks.json
```

---------------------------------------------
###### _Tor Browser is required to be open and running in the background in order for the electrum tor wallet to connect._
---------------------------------------------




## 2.) Getting Started With Windows


##### 1.) Download this repo as a zip and extract it to where you would like it to run from: 
https://github.com/vergecurrency/electrum-xvg-tor/archive/master.zip

##### 2.) Download and install python 2.7 for windows here: 
https://www.python.org/ftp/python/2.7.10/python-2.7.10.msi

##### 3.) Download and install Microsoft Visual C++ Compiler for Python 2.7 here: 
https://www.microsoft.com/en-us/download/details.aspx?id=44266

##### 4.) Download and install python qt4: 
http://sourceforge.net/projects/pyqt/files/PyQt4/PyQt-4.11.3/PyQt4-4.11.3-gpl-Py2.7-Qt4.8.6-x64.exe

##### 5.) Launch MS Visual Studio command prompt (32 or 64 bit) 

##### 6.) cd into the directory electrum-xvg-tor-master and execute the following:

```
pyrcc4 icons.qrc -o gui/qt/icons_rc.py
```

```
python -m pip install --upgrade pip
```

```
python -m pip install pyasn1 pyasn1-modules pbkdf2 tlslite qrcode ecdsa ltc_scrypt
```

```
python setup.py install
```

```
python electrum-xvg
```


## 2.b) Installing TOR Browser

#### 1.)
#### Options 1: download Tor browser here:

https://www.torproject.org/download/download-easy.html.en#windows

#### Option 2: If you are in a location where access to the Tor Project website is blocked:

##### You can request a copy of the Tor Browser Bundle installer via email. 

##### To do this, send an email to gettor@torproject.org with the version of Tor you want in the body of the email (e.g., Windows if you have a Windows computer, OSX if you use a Mac Computer, or Linux if you use a Linux-based computer).

##### You will receive a reply to your email with a link to download the installer via several locations online.


#### 2.) Execute the file you downloaded to extract the Tor Browser into a folder on your computer.

#### 3.) Create a shortcut to Tor browser on your Desktop

#### 4.) Then simply click on “Start Tor Browser.”

---------------------------------------------
###### _Tor Browser is required to be open and running in the background in order for the electrum tor wallet to connect._
---------------------------------------------



## 3.) Installing On OS X

#### Install The Following Dependencies:

1.)
####  _(open a terminal window)_
###### xcode
```
xcode-select --install
```

###### Homebrew:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

###### Python:
```
brew install python@2
```

###### Modify your system $PATH variable to point to the latest version of python:
```
export PATH="/usr/local/opt/python@2/sbin:${PATH}"
```

###### pip
```
sudo easy_install pip
```

###### slowaes
```
sudo pip intall slowaes
```

###### Tor
```
brew install tor
```

###### Edit the sample Tor configuration file:

```
cd /usr/local/etc/tor
```

```
sudo nano torrc.sample
```

###### Remove the # before the line that starts with SocksPort 9050: 

Before:
```
## Tor opens a SOCKS proxy on port 9050 by default -- even if you don't
## configure one below. Set "SOCKSPort 0" if you plan to run Tor only
## as a relay, and not make any local application connections yourself.
#SOCKSPort 9050 # Default: Bind to localhost:9050 for local connections.
#SOCKSPort 192.168.0.1:9100 # Bind to this address:port too.

```

After:
_(should look like this)_
```
## Tor opens a SOCKS proxy on port 9050 by default -- even if you don't
## configure one below. Set "SOCKSPort 0" if you plan to run Tor only
## as a relay, and not make any local application connections yourself.
SOCKSPort 9050 # Default: Bind to localhost:9050 for local connections.
#SOCKSPort 192.168.0.1:9100 # Bind to this address:port too.

```

###### Rename and Save the file:

```
CTRL+X > Y 
```
Rename the file to 'torrc' by deleting .sample
```
ENTER > Y
```

###### Restart tor: 

```
sudo service tor restart
```


#### 3.) Clone the electrum-xvg-tor Repository to your Documents folder:
```
cd ./Documents
```

```
git clone https://github.com/vergecurrency/electrum-xvg-tor && cd electrum-xvg-tor
```

```
python setup.py build
```

```
sudo python setup.py install
```

#### Launch the wallet:

```
python electrum-xvg
```



## 3.b) Installing TOR Browser

#### 1.)

#### Options 1: download Tor browser here:

https://www.torproject.org/dist/torbrowser/7.5.3/TorBrowser-7.5.3-osx64_en-US.dmg

#### Option 2: If you are in a location where access to the Tor Project website is blocked:

##### You can request a copy of the Tor Browser Bundle installer via email. 

##### To do this, send an email to gettor@torproject.org with the version of Tor you want in the body of the email (e.g., Windows if you have a Windows computer, OSX if you use a Mac Computer, or Linux if you use a Linux-based computer).

##### You will receive a reply to your email with a link to download the installer via several locations online.


#### 2.) Navigate to the folder in which you saved the Tor Browser package (a .dmg file beginning with 'Tor Browser'). In this example, we assume you saved file in your Downloads file.

#### 3.) Double-click the Tor Browser .dmg file to mount it as a disk image. It should show up as in a new window and under Devices in the left-hand sidebar of a normal Finder window.

#### 4.) Drag the TorBrowser.app into your Applications folder.

#### 5.) Before we start using TorBrowser, we should unmount (or 'eject') the TorBrowser disk image. Find Tor Browser under Devices in the Finder sidebar. Click on the {eject} icon next to it in the sidebar to unmount the disk image.




## 3.c) How To Configure TOR Browser.


##### 1.)  Navigate to the Tor Browser in your Applications folder and open the application.

#### 2.)  Depending on your security settings in System Preferences, you may now see a notification telling you that Tor Browser is from an ’unidentified developer’.

###### 2.1) Open System Preferences by clicking on the Apple icon in the top-level menu and scrolling down to select System Preferences.

###### 2.2) Click on Security & Privacy in the top row of System Preferences.

###### 2.3) In the Security & Privacy section of System Preferences, you should see your Gatekeeper settings in the bottom half of the window. 

###### 2.4) You will see "TorBrowser.app" was blocked from opening because it is not from an identified developer. 

###### 2.5) Select "Open Anyway"

#### 3.) Upon opening Tor browser you will be prompted to either 'connect' or 'configure'

###### 3.1) To connect directly to the Tor network, click [Connect].




## 3.d) Configure TOR Bridges (OPTIONAL)


##### 1.) Click the Configure button to use a bridge or proxy to connect to Tor.

##### 2.) In the next window, Select Yes.

##### 3.) Next, select the default obfs4 bridge.

##### 4.) The next window asks you if you need to use a local proxy to access the Internet. Normally you can connect the Tor network via Tor bridge so just select No.


After that, the Tor browser will try to establish a connection to the Tor network.


---------------------------------------------
###### _Tor Browser is required to be open and running in the background in order for the electrum tor wallet to connect._
---------------------------------------------




## 4.) How Official Packages Are Created.

### On Windows:
```
python mki18n.py

pyrcc4 icons.qrc -o gui/qt/icons_rc.py

python setup.py sdist --format=zip,gztar
```
### On Mac OS X:

#### On port based installs:
```
sudo python setup-release.py py2app
```
#### On brew installs:
```
ARCHFLAGS="-arch i386 -arch x86_64" sudo python setup-release.py py2app --includes sip

sudo hdiutil create -fs HFS+ -volname "Electrum-XVG" -srcfolder dist/Electrum-XVG.app dist/electrum-xvg-VERSION-macosx.dmg
```

