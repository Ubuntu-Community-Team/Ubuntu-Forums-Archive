---
title: "Brother DCP 750CW top margin not present"
date: 2010-09-16
forum: Hardware
---

### Post by jaaf64 on 2010-09-16
Hi,

I have been using a brother DCP 750CW printer on Ubuntu with no problem  for years.
Recently after having installed 10.4, I discovered that the top margin disappears and that the text of my page is shifted close to the egde of the paper sheet.
I installed the drivers using synaptic. My printed is connected via Ethernet.
The problem is the same for both 64 bits and 32 bits version.
Is this problem known.
I need some help

---

### Post by jaaf64 on 2010-09-17
Eventually I could manage to install it correctly on 64 bits Ubuntu 10.4.
It was not easy as I couldn't find any exact procedure somewhere
I would like to write some howto in order to help others but I don't know where to do so!

---

### Post by Carl.Spackler on 2010-09-18
I have a MFC-6490CW and wrote a small shell script (nothing pretty at all, but it works) to determine the version of the OS, modify app-armor, get the extra packages and install the packages as well as modify the scanner document creation mode. I put the files that I downloaded from Brother support into a subdirectory beneath the script called brother. I also created the "brscan-skey.desktop" file to setup the autostart entry for ScanKey application and created a file called "scantofile-0.2.1-3.sh" to change the JPG format of a scan to PDF. I put those into the same subdirectory.
 
Not sure if you can use it, but here it is. Hope it helps.
 
Main script:
 
```

 
# INSTALL BROTHER MFC-6490CW PRINTER
clear
 
### Get architecture to install correct binaries
ARCH=$(dpkg --print-architecture)
echo "Your architecture is" $ARCH
sleep 1
 
### Do main installation for both platforms
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
sudo ln -s /etc/init.d/cups /etc/init.d/lpd
sudo mkdir /var/spool/lpd
sudo apt-get -y install tcsh csh sane-utils netpbm
if [ "$ARCH" = "amd64" ];
then 
echo Installing AMD64 specific packages...
sudo apt-get -y install ia32-libs
sudo dpkg -i --force-all ./brother/brscan3-0.2.7-1.amd64.deb
sudo dpkg -i --force-all ./brother/brscan-skey-0.2.1-3.amd64.deb
elif [ "$ARCH" = "i386" ];
then
echo Installing i386 specific packages...
sudo dpkg -i --force-all ./brother/brscan3-0.2.7-1.i386.deb
sudo dpkg -i --force-all ./brother/brscan-skey-0.2.1-3.i386.deb
else 
echo "Your CPU architecture is not compatible with this installation" 
exit
fi
echo Installing the remaining packages now...
 
### Install the rest
sudo dpkg -i --force-all ./brother/mfc6490cwlpr-1.1.2-2.i386.deb
sudo dpkg -i --force-all ./brother/mfc6490cwcupswrapper-1.1.2-2.i386.deb
sudo dpkg -i --force-all ./brother/brmfcfaxlpd-1.0.0-1.i386.deb
sudo dpkg -i --force-all ./brother/brmfcfaxcups-1.0.0-1.i386.deb
 
### Setup scanner with current configuration
brsaneconfig3 -a name=Brother model=MFC-6490CW ip=10.1.1.5
 
### ScanKey tool install
mkdir ~/.config/autostart
chmod 700 ~/.config/autostart
cp ./brother/brscan-skey.desktop ~/.config/autostart/
chmod 644 ~/.config/autostart/brscan-skey.desktop
 
### Fix scanner filter permissions
sudo chmod 755 /usr/lib/cups/filter/brfaxfilter
sudo service cups restart
sudo chmod 777 /usr/local/Brother/sane/brscan-skey-0.2.1-3.cfg
 
### Change default scantofile file type to PDF (Added 4/25/2010)
sudo cp ./brother/scantofile-0.2.1-3.sh /usr/local/Brother/sane/script/
sudo chown root.root /usr/local/Brother/sane/script/scantofile-0.2.1-3.sh
 
### Clean-up root directory from alien package trash
sudo rm /brmfcfax*.*
 
### Launch Firefox to complete Printer & Fax installation
firefox "http://localhost:631/printers" &
 
### END BROTHER PRINTER INSTALL ###
 

```
 
brscan-skey.desktop file:
 
```

 
[Desktop Entry]
Type=Application
Exec=/usr/bin/brscan-skey
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Brother ScanKey
Name=Brother ScanKey
Comment[en_US]=Brother ScanKey Application
Comment=Brother ScanKey Application
 

```
 
scantofile-0.2.1-3.sh file:
 
```

 
#! /bin/sh
set +o noclobber
#
# $1 = scanner device
# $2 = friendly name
#
# 
# 100,200,300,400,600
#
resolution=100
device=$1
mkdir -p ~/brscan
if [ "`which usleep`" != '' ];then
usleep 10000
else
sleep 0.01
fi
output_file=`mktemp ~/brscan/brscan.XXXXXX`
chmod 644 $output_file
echo "scan from $2($device) to $output_file"
#scanimage --device-name "$device" --resolution $resolution> $output_file
scanimage --device-name "$device" --resolution $resolution | pnmtops | gs -q -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=- - > $output_file.pdf
 

```

---

### Post by jaaf64 on 2010-09-19
Thank you.

As I told you, I have managed to install it eventually. 
I am not very clever at scripting but reading you script, it seems to me that it would works with my printer as all the small imperfections in Brother's guide are covered.

I need to install Ubuntu on an other computer so I will try your script to install the printer within a few days.

---

