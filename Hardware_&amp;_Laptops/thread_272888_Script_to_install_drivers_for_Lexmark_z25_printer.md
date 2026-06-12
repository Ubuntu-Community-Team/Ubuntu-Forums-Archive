---
title: "Script to install drivers for Lexmark z25 printer"
date: 2006-10-07
forum: Hardware &amp; Laptops
---

### Post by motstudios on 2006-10-07
Greetings!

    I've been trying for a week to get a Lexmark z25 printer to work. Well I finally did and wanted to help those who also are having problems with getting a Lexmark z25 printer to work. To make it as easy as possible for the user, I made a bash script that will download the official drivers, convert them to a useable format and then install them. The user must still setup their printer using whatever tool Ubuntu, Kubuntu, Xubuntu has.

    I've tested this script and it works for me on Xubuntu and now my printer works almost perfectly. Also note, I'm testing another script I'm working on that will install many commonly requested applications, libs, codecs, compiling apps java, flash and more. This other script will also have the option to install the Lexmark z25 drivers. 
If you want to test this other script I'm working on, you can get it at [http://mark.22kb.com/dl/ubuntu/](http://mark.22kb.com/dl/ubuntu/) just look for a tar.gz file called Ubuntu-Install-Script-<VERSION>-<RELEASE>.tar.gz
where <VERSION> is either Dapper or Edgy and <RELEASE> is the version number of the script. Get the highest version number for the script.

---------------------------------------------------------------
PLEASE MAKE SURE DEPENDENCIES ARE MET!

Dependencies:
sudo apt-get install alien        # rpm to deb converter
sudo apt-get install libstdc++5   # (need v5 for compatibility)

1. Make sure the dependencies are met (see above).

2. Download the bash script I made (Right Click, Save As): [http://mark.22kb.com/dl/lexmark-z25-z35.sh](http://mark.22kb.com/dl/lexmark-z25-z35.sh)

3. Copy the bash script to your /home/username directory

4. Open a terminal and run the following commands:
cd /home/yourusername
sudo chmod u+x lexmark-z25-z35.sh
sudo ./lexmark-z25-z35.sh

5. Once the script is finished, Set up your printer using the new driver.
In UBUNTU/GNOME -- System->Administration->Printing)
In XANDROS Launch-> Control Center -> Peripheral Devices-Printers

MORE NOTES: If you don't trust the bash script, open it with a text editor and take a look. It just performs all the commands the user would have to do. It makes it much easier to get your z25-z35 printer working.

---

