---
title: "Limewire"
date: 2006-01-18
forum: Installation &amp; Upgrades
---

### Post by nee coa la on 2006-01-18
Well the only version of limewire for Linux is an RPm file. IS there a way to install that? or is there another version I am not aware of? What should I do?

---

### Post by StubornAH on 2006-01-18
Just a quick thought, but isn't RPM a Redhat upgrade.  I once read through a Redhat book to learn a little more about Linux and Redhat claims they have a very good update program and that other distributions have used theirs or made something similar.  So, if you are into research I would start there.

---

### Post by nee coa la on 2006-01-18
Well the way i look at it is this: 

there are thousands of linux pros on this forum. I am hoping somone can save me a little reading. ;-)

---

### Post by sabitha on 2006-01-18
why dont try this :

first you must have java plugins instaled
then :
wget -c [http://frankandjacq.com/ubuntuguide/LimeWireSoftOther.zip](http://frankandjacq.com/ubuntuguide/LimeWireSoftOther.zip)
sudo unzip -u LimeWireSoftOther.zip -d /opt/
sudo chown -R root:root /opt/LimeWire/
sudo gedit /usr/bin/runLime.sh

replace this on that new file :

cd /opt/LimeWire/
./runLime.sh

save the file 

sudo chmod +x /usr/bin/runLime.sh
sudo gedit /usr/share/applications/LimeWire.desktop

replace this :

[Desktop Entry]
Name=LimeWire
Comment=LimeWire
Exec=runLime.sh
Icon=/opt/LimeWire/LimeWire.ico
Terminal=false
Type=Application
Categories=Application;Network;

save the file
then 

killall gnome-panel 

done !!! :razz:

---

### Post by manicka on 2006-01-19
Alternatively you could try Frostwire.. the free clone of Limewire

new deb released a few days ago

[http://www.frostwire.com/index.php?title=FrostWire:Download](http://www.frostwire.com/index.php?title=FrostWire:Download)

---

### Post by nee coa la on 2006-01-19
okay well im unsure as to how I install it. I downloaded it but im not sure what to do now...i know i know. but ive been a windows user for years.

---

### Post by HJThis on 2006-01-19
Hello,nee coa la & Welcome

Well if you downloaded the file to say home dir
just open a Terminal & do this here

dpkg -i FrostWire-4.10.3-0-i586.deb

hit enter you may need to use sudo

but here is a link that for me made installing
some great software without one problem

[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

just like to add using the above link i installed 
Frostwire firefox1.5 & then some with no problems

Best of luck

---

### Post by nee coa la on 2006-01-19
wow thanks that worked!

---

### Post by HJThis on 2006-01-19
Hi,nee coa la

First it's great to know someone from Mass is here

now make sure to install 

chkrootkit & rkhunter they will both scan your Box 
for Rootkit's

& some say you don't need a virus scanner on
linux but i have 2 one as a back-up incase the
first one finds anything

but i use a virus scanner not because of the net
but for my dumb bass brother's like to play games

oh & don't for get to install Firestarter

To install progs just goto

System >> Administration >> Synaptic Package Manager
then just do a Search for the progs to install

if you need any help with the progs let us know
or do a Search for How tos

Best of luck

---

### Post by nee coa la on 2006-01-19
Awesome thanks man. 

By the way, where abouts are you in Mass?

---

### Post by cvmostert on 2006-02-04
Great! I just installed frostwire and it works better then the others i have tried... gnutella... works for me...

---

### Post by Ubuntuud on 2006-02-04
It isn't so hard to install RPM.
First you need to install "alien", this can be done through synaptic, but "sudo apt-get install alien" does the same.
Then put the file on your desktop, get back to the command line and type "cd Desktop", then type "sudo alien <name of the file>.rpm".
A new file will be created with the ".deb" extension.
Type "sudo dpkg -i <name of the file>.deb" and the program will be installed.

---

