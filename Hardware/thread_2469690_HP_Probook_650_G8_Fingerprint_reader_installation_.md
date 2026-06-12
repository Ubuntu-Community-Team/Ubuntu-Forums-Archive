---
title: "HP Probook 650 G8 Fingerprint reader installation guide"
date: 2021-12-06
forum: Hardware
---

### Post by vukasin-nuhijevic on 2021-12-06
Hello,

I recently bought HP Probook 650 G8 and I wanted to make everything work. Ubuntu 20.04.3 is working out of the box, but fingerprint reader is not enabled. After some research and work I managed to enable and to use fingerprint reader. I want to share with you how to enable fingerprint reader.


[LIST]
[*]Fingerprint device is ID 06cb:00f0 Synaptics, Inc. -> it is supported by last version of libfprint 
[/LIST]


[LIST]
[*]Initial FW of this device didn't support Linux, but there is an update. So now we have to update fingerprint reader
[LIST]
[*]tool for that is fwupdmgr, but ubuntu 20.04 version has a problem and won't update device as it should. So it is important to use snap version of fwupd:
[LIST]
[*]sudo apt purge fwupd
sudo apt autoremove
snap install fwupd --classic
fwupdmgr get-devices
fwupdmgr get-updates
fwupdmgr update
[/LIST]
[/LIST]
[/LIST]



[LIST]
[*]install one dependency
[/LIST]
 [INDENT]sudo apt install -y gir1.2-gusb-1.0[/INDENT]
 
 
[LIST]
[*]Unfortunately, Ubuntu has only 1.90 version of libfprint, which does not support this reader. We have to build new packages. I found a tutorial which is working:
[LIST]
[*][https://community.frame.work/t/fingerprint-scanner-compatibility-with-linux-ubuntu-fedora-etc/1501/131](https://community.frame.work/t/fingerprint-scanner-compatibility-with-linux-ubuntu-fedora-etc/1501/131) 
[*]One change has to be made: instead of goodixmoc use synaptics:
[LIST]
[*]CONFIG_ARGS = \
    -Dudev_rules_dir=/lib/udev/rules.d \
    -Dgtk-examples=false \
    -Ddrivers=synaptics 
[/LIST]
  
[*]build and install packages 
[/LIST]
  
[*]Enable and start the service:
sudo systemctl enable fprintd.service
sudo systemctl start fprintd.service 
[/LIST]


[LIST]
[*]Activate the PAM module:
sudo pam-auth-update --enable fprintd 
[/LIST]



[LIST]
[*]Enroll Fingerprint: 
[/LIST]
[INDENT]fprintd-enroll
[/INDENT]

Now you can enjoy your fingerprint reader 8-)

I have built packages and if you are lazy here is the link:
[https://file.io/eza2O4V5w15F](https://file.io/eza2O4V5w15F)



Bye,
Vukasin

---

