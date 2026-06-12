---
title: "PS3 Xubuntu + Sound + Bluetooth + WiFi/WPA: working!"
date: 2008-09-18
forum: General Help
---

### Post by yuri_rage on 2008-09-18
[SIZE="1"]This is my first new thread at ubuntuforums, so apologies if it's in the wrong location.[/SIZE]

**First, a few words about my intent:**
There are A TON of online resources describing Linux configuration on the PS3, but none of them are very complete, and many of them have misinformation.  Additionally, many of the HOW-TO documents online are outdated by over a year, so they are of limited use.  So, this post is **[COLOR="Red"]current as of 17 Sep 2008[/COLOR]**, and, due to personal time constraints, I do not intend to maintain it with constant edits and updates (though I may answer a few initial questions and comments).

**Your experience level:**
If you intend to get a fully functional PS3 Linux system, you should be familiar with Linux already and have a basic grasp of the operating system, its quirks, and, particularly, the command line interface.  Even so, you are inviting frustration by expecting a truly useable Linux system on your PS3.  If this is your first Linux install, be prepared for a few hours of boredom punctuated by fits of rage.  I take no responsibility if your PS3 is "bricked" after any custom software build/install.

**My system:**
80GB PS3 (two USB ports, non-PS2 compatible), Xubuntu 7.10 upgraded to kernel 2.6.25.4, Logitech Mediaboard Pro Keyboard, USB mouse, WPA enabled wireless network, Toshiba 46HM95 TV (connected to PS3 via HCMI)

**What you need:**
A PS3 and an install CD
A USB keyboard (and preferably a mouse - note: Bluetooth won't work for the installation)
The ability to (temporarily) connect your PS3 to a wired network
Time (several hours, minimum)

**Useful items:**
A removable USB drive (memory stick)
A USB hub to expand the PS3 ports
Another Linux machine on the local network
Patience

**Xubuntu install:**
First, [install Xubuntu 7.10]("https://help.ubuntu.com/community/PlayStation_3").  I'm not going to get into details here.  The online instructions are quite adequate.  Xubuntu is my preferred install.  YDL is optimized for the cell architecture but has limited packages and support.  *buntu distributions are well documented and have thousands of binary packages available along with a solid support community.  Xubuntu runs relatively fast and detects most hardware automatically.

**[COLOR="Red"]Connect your PS3 to a wired network for these steps:[/COLOR]**

**Kernel update:**
Next, update the kernel.  The files at [http://kernel.org/pub/linux/kernel/people/geoff/cell/](http://kernel.org/pub/linux/kernel/people/geoff/cell/) provide the most up-to-date kernel packages available.  However, they may be unstable, so use them with caution.  Instructions and a bash script for updating the kernel are available on page 4 of this thread: [http://psubuntu.com/forums/viewtopic.php?f=4&t=161&st=0&sk=t&sd=a&start=30](http://psubuntu.com/forums/viewtopic.php?f=4&t=161&st=0&sk=t&sd=a&start=30).  Note that you will have to re-install the otheros.bld file from the PS3 OS after updating the kernel, or it will hang at shutdown/reboot.

**otheros.bld update:**
To update/install another otheros.bld, copy it to a removable USB drive under the filename /PS3/otheros/otheros.bld.  Insert the drive into the PS3, and start the game OS.  Select Install Other OS under System Settings (don't worry, it only over-writes the boot-loader, not the entire Linux install).  You'll have to reset "Other OS" as the default system each time you boot to the game OS.

**Sound:**
At this point, sound should be working.  If it's not, try typing "alsamixer," into a command prompt, and adjusting the volume.

**petitboot:**
If, like me, you want to avoid swapping your only USB keyboard between your desktop PC and your PS3, you'll need a spare USB mouse.  Then install [petitboot]("http://www.ozlabs.org/~jk/projects/petitboot/") using the instructions above for installing an updated otheros.bld.  If you use petitboot 0.2 with kernel 2.6.25.4, you won't have any issues with the shutdown/reboot sequence.  Now you should be able to use the mouse to select boot OS.  I've found that petitboot USB PS3 controller functionality is intermittent at best, despite the documentation that states otherwise.

**Bluetooth:**
[FONT="Courier New"]sudo apt-get install bluez-utils[/FONT]
Set up [FONT="Courier New"]/etc/bluetooth/hcid.conf[/FONT].  Mine looks like this:
```

# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x000100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

```
Adding the line:
[FONT="Courier New"]hidd --search[/FONT]
to [FONT="Courier New"]/etc/rc.local[/FONT] may increase the chances that your device(s) will be found on boot.  Putting devices into connection mode during the boot sequence seems to help.  If you can find out the hardware address of the device in question (try sudo hidd --search), you can use this command to force a connection:
[FONT="Courier New"]sudo hidd -i AB:CD:EF:12:34[/FONT]
(replace [FONT="Courier New"]AB:CD:EF:12:34[/FONT] with the hardware address)
I have about 75% success with Bluetooth connectivity at boot-up.  That can be irritating, so see the next step (not a fix, just a work-around).

**(optional) Install an ssh server:**
[FONT="Courier New"]sudo apt-get install openssh-sever[/FONT]
Now you can ssh into the PS3 and use hidd commands to fix Bluetooth devices that don't want to connect on their own.  This was particularly useful for me, since my only USB keyboard is connected to my everyday desktop machine, but I have a Logitech Bluetooth keyboard that works great for the PS3.  If the PS3 fails to connect to the Bluetooth keyboard at boot time, I can ssh into the PS3 from another machine on the network and get the PS3 to connect to the Bluetooth keyboard by issuing:
[font="Courier New"]sudo hidd --search[/font]

**WiFi/WPA &#8211; possibly the most frustrating portion**
[FONT="Courier New"]sudo apt-get install build-essential gcc-4.1-multilib[/FONT]
Then download this source code: [http://rapidshare.com/files/94642689/hostap-0.6.2.tar.gz.html](http://rapidshare.com/files/94642689/hostap-0.6.2.tar.gz.html)
Then (in a terminal window):
[FONT="Courier New"]
tar xzf hostap-0.6.2.tar.gz
cd hostap-0.6.2/
patch -p1 <add-ps3-driver.patch
cd wpa_supplicant/
make
sudo aptitude hold wpasupplicant[/FONT]

Now replace the binaries in [FONT="Courier New"]/sbin[/FONT] with the ones you just created with the "make" command.  Use this command to find the encrypted key for your setup:
[FONT="Courier New"]wpa_passphrase <ssid> [passphrase][/FONT]
Where [FONT="Courier New"]<ssid>[/FONT] is your wireless network name, and [FONT="Courier New"][passphrase][/FONT] is the key.  Note that [FONT="Courier New"]<ssid>[/FONT] is case sensitive.  Paste the result into the [FONT="Courier New"]/etc/network/interfaces[/FONT] configuration file.  For example:
```

# wpa_passphrase WRT54G wrt54gwrt54gwrt54g
network={
	ssid="WRT54G"
	#psk="wrt54gwrt54gwrt54g"
	psk=be94d7bf41abe3cd3d922e7b11f9861bdd15e05c3a8c5dae12d096990e7de166
}

```
Here is my [FONT="Courier New"]/etc/networking/interfaces[/FONT], using the example info above:
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto wlan0_rename
iface wlan0_rename inet dhcp
wpa-driver ps3
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid WRT54G
wpa-psk be94d7bf41abe3cd3d922e7b11f9861bdd15e05c3a8c5dae12d096990e7de166

```
The commands, [FONT="Courier New"]ifconfig[/FONT] and [FONT="Courier New"]iwconfig[/FONT], may help in determining the device names, in case yours differ from [FONT="Courier New"]eth0[/FONT] and [FONT="Courier New"]wlan0_rename[/FONT].  Don't bother downloading other GUI network admin tools, and don't bother using the Xubuntu built-in network-admin tool.  The file above does not enable wired network access.  Your access point must be set up with WPA (Personal) / TKIP / shared key (not WPA2).  You can get immediate results by typing:
[FONT="Courier New"]sudo /etc/init.d/networking restart[/FONT]
instead of rebooting.

**[COLOR="Red"]With any luck, you should now be able to disconnect the ethernet cable and operate wirelessly.[/COLOR]**

**Other useful tips:**

If you want to use nfs, these are the packages:
[FONT="Courier New"]sudo apt&#8211;get install nfs-common portmap[/FONT]
See man pages for mounting shares.

amarok using a shared library from another machine:
[Set up amarok + mysql on host machine.]("http://amarok.kde.org/wiki/MySQL_HowTo")
[Enable mysql networking on host machine.]("http://kb.parallels.com/en/1134")
[FONT="Courier New"]sudo apt-get install amarok[/FONT]
Disable amarok's folder monitoring feature on the PS3.  Mount the shared library using the exact same path as on the host machine.  Consider using a wrapper script to inhibit starting amarok if the shared library is not available (to avoid a connection to the mysql database that may wipe it clean, since the client machine won't find any of the associated files).

ps3videomode &#8211; if your TV doesn&#8217;t support overscan options, there isn&#8217;t a good solution for full screen mode (you'll always have black borders or a portion of the desktop outside the viewable area).

If the TV is less then about 60&#8221;, web browsing from a normal TV viewing distance is of limited use.  Adjusting system fonts and browser settings can make it useable.  Flash and other plugins have limited support.

---

### Post by Raimond on 2008-09-21
well I knew it would be complicated... but at least now I'm a bit more prepared...

Thanks a lot. :)

---

