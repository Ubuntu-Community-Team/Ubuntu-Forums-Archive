---
title: "Canoscan LIDE 90"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by silvanus2005 on 2008-02-29
I am running Ubuntu 7.10 on a Toshiba Satellite laptop, but I cannot make work my scanner, an Canoscan LIDE 90. Is there a way to making it work in Ubuntu?

---

### Post by linuxwizard on 2008-02-29
According to this > [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) > unsupported.

---

### Post by silvanus2005 on 2008-03-09
Yes, I knew that when I posted on forum. Is there a way to make work by installing a new Linux kernel? A friend of mine told me to do so, but I wanted to ask if I can find what drivers are provided in the new kernel, before doing anything. thx.

---

### Post by linuxwizard on 2008-03-09
No, it is not supported by Sane. Installing a new kernel not going to help.

---

### Post by silvanus2005 on 2008-03-09
I understand. Is there a way to scan using Windows drivers from Ubuntu? I read sometjing about using Wine for that, but I didn&#8222;t understand well how to do that.

---

### Post by rbrown3rd on 2008-05-04
There is work in progress by the guys that are involved in Sane to get a driver working.  Meanwhile I have mine working on my laptop using my Virtualbox Winxp install.  I just started my virtualbox WinXP machine and installed the Canon driver.  So, it does work like that but I have not tried Wine yet.  Also, I am a relatively new user of Kubuntu and by no means an expert.

---

### Post by silvanus2005 on 2008-05-12
Can you tell me how to install Virtualbox on my laptop? May I found it searching through packages using synaptic?

---

### Post by crusher_of_c on 2008-05-16
Hey,

I am a new user so I can't help you much with my own knowledge; however, I have compiled a little how-to for myself from advice of many other users. I hope the people who I am copying from (I unfortunately did not take down their names) won't mind. I use a 64 bit processor so some of the info is for amd64; however, there is still plenty of good info. Try and scan over all of it. I did do this and it worked so I can answer some questions, but trust me, not many.

Here it is:

		**Links:**

[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)		

		[B]Downloading:
[/B]
[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb)

[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb)
		

		**Installation:**

Add yourself to the group VirtualBox created during install called "vboxusers" The VB install creates this group, find it, don't add another one.

Create a group named "usbusers" and put yourself in it.

sudo groupadd usbusers
sudo gpasswd -a <yourusername> usbusers

Or do the above in Control Center under 'users and groups'.

Now uncomment the 4 lines below 'Magic to make /proc/bus/usb work' in mountdevsubfs.sh , they will be commented out by default) so it looks like the following:

sudo gedit /etc/init.d/mountdevsubfs.sh

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Now then,

Modify the rules in file "/etc/udev/rules.d/40-permissions.rules"
Change the lines :

From:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

To :

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="usbusers", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

In Hardy Heron, I had to add the lines at the end of the file (under To: above) as this file is different in Hardy Heron, that is you won't see the 'from' lines above like you will in Gutsy.

The Grande Finale,

add this line:

none /proc/bus/usb usbfs devgid=120,devmode=664 0 0

to your /etc/fstab file (at the bottom). Just make sure that 120 is your vboxusers group (use your own number).


Reboot the computer.

Open VirtualBox and click on "Settings".

Click on the "USB" item in the left pane to edit the USB prefs.

Click on the "Add device" button to add a filter and select your printer from the list and click on the "Ok" button.

Start your VM and Windows should detect your printer.

The above was taken mostly from various scattered posts in the Ubuntu forums, some from me, and put together here, all mods in one place, in order, for future reference.

If you have a problem getting the usb devices recognized in VB, please post here. Potential edit recommendations are welcomed.


		**Network Communication:**

From the VirtualBox's menu, go to Devices &#8594; Shared Folders... to add/remove the folders of the host operating system that you would like to share with the guest operating system (Windows XP, in this example). When done click Ok.

Now we are going to access the folders we added. DO NOT open My Network Places! Instead open a new explorer instance. You can do that by pressing WinKey-E or by executing the explorer command (Start &#8594; Run... &#8594; type "explorer" &#8594; Ok). You should see a windows that looks like this:

windows explorer screenshot

Now, carefully click on the expand icon (expand icon) right next to My Network Places. Make sure you click exactly on the expand icon. If you accidentally clicked on My Network Places, you ruined everything and you will have to go back and start all over again. After expanding the My Network Places branch, you should be able to see Entire Network right underneath:

windows explorer screenshot

Now expand the Entire Network branch, too, and you should be able to see VirtualBox Shared Folders:

windows explorer screenshot

Open VirtualBox Shared Folders. Normally, you should be able to see your shared folders in there.

---

