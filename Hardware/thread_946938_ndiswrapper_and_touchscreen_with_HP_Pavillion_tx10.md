---
title: "ndiswrapper and touchscreen with HP Pavillion tx1000, help?"
date: 2008-10-13
forum: Hardware
---

### Post by MaJoRa on 2008-10-13
First I would like to say what a fantastic support forums Ubuntu seems to have, I have been using it for nearly 3 years and to my knowledge have never had to post on these forums even once... although I have searched all over these forums and numerous others, and I have used guides from places I cannot even remember. I have got the fingerprint reader working fantastically, the audio works, ethernet works and the graphic drivers are far better than that of Hardy Heron.

Here is my problem, I am using Ubuntu 8.10 Beta, I wish to get my wireless and touchscreen working. The first I have been partially sucessful in doing using the following guide:
[http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm)

That will enable my wireless, until I reboot, at which point I have to perform the entire set of commands over... this is rather annoying since it says the last command is supposed to stop that from happening... Any advice?

The latter of which I have had no success either way, in fact I have used not only that guide but countless others and I just seem to be getting no response from my touchscreen at all. This disappoints me because in Fiesty Fawn I got it functioning 100% fist time, but with Hardy Heron I could only get it to work (no matter what I seemed to try) using TouchKit, and it would only click where my mouse already was (it failed to move it).

If it helps anyone to know who might be able to help me I am running the 64bit Ubuntu.

I hope to get this resolved as soon as possible but I understand not everyone has the time to, so I thank anyone who can help or who offers their help in advance.

---

### Post by edmondt on 2008-11-06
I second that... 8.10 runs on X.Org X Server 1.5.2 and the TouchKit driver only supports Kernel 2.6.x with xorg 1.4.0.90 according to [http://home.eeti.com.tw/web20/TouchKitDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/TouchKitDriver/linuxDriver.htm)

I guess we have to either wait, or if someone has a solution, please post and share :)

---

### Post by gali98 on 2008-11-07
I can't help on the touchscreen, but for the wireless:
1. what kind of card is it (broadcom, etc)
2. Have you tried restricted drivers?
Kory

---

### Post by Thelazygoose on 2008-11-19
yes, i am having the same problem. I have a tx1000 and had the wireless working with 7.10 using the tut from the "helpful tips for tx1000" forum, but when upgrading to 8.04 it wouldn't work. so i upgraded to 8.10 and am now looking for a way to get it to work. anyone who could help me i would really appreciate it.

---

### Post by vishalrao on 2008-11-22
did the "Broadcom STA" driver thru restricted driver manager not work for you? Worked for me for my tx1302au.

Also for touchscreen see : [http://ubuntuforums.org/showthread.php?t=983773](http://ubuntuforums.org/showthread.php?t=983773)

mailing list post: [https://lists.ubuntu.com/archives/ubuntu-in/2008-November/004221.html](https://lists.ubuntu.com/archives/ubuntu-in/2008-November/004221.html)

---

### Post by twrock on 2009-03-14
I'm reviving this thread.

Did anyone ever get the touchscreen working for 8.10?

Thanks.

---

### Post by Favux on 2009-03-14
Hi twrock,

Post #6 on this thread?

[http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000]("http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000")

---

### Post by championswimmer on 2010-05-06
**[COLOR=red]Installing UBUNTU 9.04 on HP TX1000 laptop (touchscreen+fingerprint)[/COLOR]**
  [COLOR=red]1.       [/COLOR][COLOR=red]Install Ubuntu 9.04 Jaunty[/COLOR]
  [COLOR=red]2.       [/COLOR][COLOR=red]Connect to Internet and open SYSTEM>ADMINISTRATION>HARDWARE DRIVERS [/COLOR]
  [COLOR=red]3.       [/COLOR][COLOR=red]Install NVIDIA current version[/COLOR]
  [COLOR=red]4.       [/COLOR][COLOR=red]Install Broadcomm B43 driver[/COLOR]
  [COLOR=red]5.       [/COLOR][COLOR=red]Install software modem driver[/COLOR]
  [COLOR=red]6.       [/COLOR][COLOR=red]Download eGalaxDriver from website [/COLOR][COLOR=#76923C][[COLOR=#76923C]http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm[/COLOR]]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm")[/COLOR][COLOR=red][/COLOR]
  [COLOR=red](download for kernel 2.6.xx)[/COLOR]
  [COLOR=red]7.       [/COLOR][COLOR=red]Extract tarball and run setup.sh from terminal with sudo[/COLOR]
  [COLOR=red]8.       [/COLOR][COLOR=red]Restart Computer and run (with Alt+F2) “eGalaxTouch” (without quotes and linux is case sensitive)[/COLOR]
  [COLOR=red]9.       [/COLOR][COLOR=red]Configure your touchscreen[/COLOR]
  [COLOR=red]10.   [/COLOR][COLOR=red]Open xorg.conf with following command[/COLOR]
  [COLOR=red][FONT=&quot]sudo gedit /etc/X11/xorg.conf[/FONT][/COLOR]
  [COLOR=red]11.   [/COLOR][COLOR=red]Under Section “Device” add the following line[/COLOR]
  [COLOR=red][FONT=&quot]Option  “RandRRotation”        “True”[/FONT][/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red]12.   [/COLOR][COLOR=red]Create two launchers on your gnome panel with following commands:-[/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red]xrandr –o 1                (for tablet mode) P.S. u can set it “3” as well if u want opposite rotation)[/COLOR]
  [COLOR=red]xrandr –o 0                        (for Laptop mode)[/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red]13.   [/COLOR][COLOR=red]Install Cellwriter from synaptic[/COLOR]
  [COLOR=red]14.   [/COLOR][COLOR=red]Install xournal from synaptic[/COLOR]
  [COLOR=red]15.   [/COLOR][COLOR=red]Install the following for finger print recognition[/COLOR]
  [COLOR=red]lib-fprint[/COLOR]
  [COLOR=red]libpam-fprint[/COLOR]
  [COLOR=red]fprint-demo[/COLOR]
  [COLOR=red]16.   [/COLOR][COLOR=red]Open file common-auth[/COLOR]
  [COLOR=red][FONT=&quot]sudo gedit /etc/pam.d/common-auth[/FONT][/COLOR]
  [COLOR=red](delete all lines in the file and paste these lines)[/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red][FONT=&quot]Auth    sufficient          pam_fprint.so[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Auth    sufficient          pam_fprint.so[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Auth    required           pam_unix.so   nullok_secure[/FONT][/COLOR]
  [COLOR=red][FONT=&quot] [/FONT][/COLOR]
  [COLOR=red](the first line can be copied 3-4 times if u want to allow more than 1 chance to register fingerprint)[/COLOR]
  [COLOR=red]17.   [/COLOR][COLOR=red]Create keyboard shortcuts for screen rotation (here is an example)[/COLOR]
  [COLOR=red]Key                                                                                        Command[/COLOR]
  [COLOR=red]Ctrl+Alt+UP                                                                       xrandr –o 0[/COLOR]
  [COLOR=red]Ctrl+Alt+LEFT                                                                    xrandr –o 1[/COLOR]
  [COLOR=red]Etc[/COLOR]
  [COLOR=red]Etc[/COLOR]
  [COLOR=red](Notes: This Guide will work for any UBUNTU installation upto Karmic (9.10). Unfortunately in Lucid, the developers have tried to provide native support for Touchsdcreen and Nvidia but it has turned out to be sloppy. And there is no xorg file as well. So viable options are to uninstall nv and nouveau drivers and install Nvidia and the run sudo nvidia-xconfig from command line. After that follow steps 4 to 17)[/COLOR]

---

