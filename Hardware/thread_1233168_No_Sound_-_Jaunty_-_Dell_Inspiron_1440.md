---
title: "No Sound - Jaunty - Dell Inspiron 1440"
date: 2009-08-06
forum: Hardware
---

### Post by count_alucard on 2009-08-06
Hi, everyone..

I'm a noob in Ubuntu.. and i just bought Dell Inspiron 1440 without any OS.. Installed Jaunty as my OS.. but there's no sound available..

here's the details of my machine audio device n codec..

1. lspci - v | less (just took the Audio Controller part)
> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Dell Device 02cf
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel2. lshw -c multimedia
>   *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
3. aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
4. cat /proc/asound/card0/codec#* | grep Codec
> Codec: IDT 92HD81B1X5
I've tried the "options snd-hda-intel model=" based on all the configurations for snd-hda-intel in ALSA-Configuration.txt but still.. there's no sound for my machine..

All volume controls slider are being set to 100%, no sounds available..

Can somebody here help me on how to troubleshoot this? Thanks in advance..
Really appreciate it if someone here can help me..

hey, guys.. i've found a solution.. i've updated my alsa driver, lib n utils.. (from 1.0.18rc3 to 1.0.20) n now i'm rolling!

---

### Post by samuel.faith on 2009-08-07
My problem is a lil bit different. I have sound, but only when I plug-in external speaker. Laptop speaker only plays the alert sounds like login sounds, but not music or anything else. Using external speakers, it works just fine.

Inspiron 1440, same config as above. Jaunty 9.04 :(

---

### Post by Pcniatic on 2009-08-08
Thanks count_alucard, I did update to alsa runing a modified script available [here]("http://ubuntuforums.org/showpost.php?p=7150907&postcount=161") (I just change the alsa version to 1.0.20) and it did work great, except for one detail, the sound comes out very low. Do you have the same issue?

EDIT: Everything is fine now. I just found a mixer for the speaker that was low on volume control.

---

### Post by johnjoy on 2009-08-14
I also have Inspiron 1440 which came pre installed with Vista. I loaded Jaunty, and sound works on and off (sound works in some reboots). I have the same config as alu_card. 
Alu_card, can you clarify how you updated lib n utils?
Please help me through steps. I'm quite new to Ubuntu.

Thanks in advance

---

### Post by vedek on 2009-08-14
> **johnjoy said:**
> I also have Inspiron 1440 which came pre installed with Vista. I loaded Jaunty, and sound works on and off (sound works in some reboots). I have the same config as alu_card. 
Alu_card, can you clarify how you updated lib n utils?
Please help me through steps. I'm quite new to Ubuntu.
 
Thanks in advance
 
hi mate you might want to create anew thread for your problem

---

### Post by count_alucard on 2009-08-15
> **johnjoy said:**
> I also have Inspiron 1440 which came pre installed with Vista. I loaded Jaunty, and sound works on and off (sound works in some reboots). I have the same config as alu_card. 
Alu_card, can you clarify how you updated lib n utils?
Please help me through steps. I'm quite new to Ubuntu.

Thanks in advance

hi, there.. u can try this guide >> [ALSA GUIDE]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/")

CHEERS!

---

### Post by johnjoy on 2009-08-19
Thanks for the help, but it didn't work

I will give the output

johnjoy@johnjoy-laptop:~$ sudo apt-get -y install build-essential ncurses-dev gettext xmlto
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
Note, selecting libncurses5-dev instead of ncurses-dev
libncurses5-dev is already the newest version.
gettext is already the newest version.
gettext set to manually installed.
xmlto is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-08-19 22:19:01--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
--2009-08-19 22:19:01--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving [email]lantic@netmon.iitb.ac.in[/email]... failed: Name or service not known.
wget: unable to resolve host address `lantic@netmon.iitb.ac.in'
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


=================================================

I am inside an institute and it has proxy. Can you tell me how to bypass this proxy, and download alsa updates.
I will be thankfull for any help.

John

---

### Post by Pcniatic on 2009-08-20
You are having problems installing fonts from Microsoft, but their are not necessary for this matter.
Continue with the other steps from the guide.

---

### Post by johnjoy on 2009-08-25
I tried to do it, but it is not working, when I tried to install alsa utils, it showed an error. Please help me

johnjoy@johnjoy-laptop:/usr/src/alsa/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.20/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.20/include'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.20/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.20/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl'
Making all in init
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl/init'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl'
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl'
make: *** [all-recursive] Error 1

What should I do?

---

### Post by johnjoy on 2009-08-25
I have noticed one thing

lspci -v|less


 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Dell Device 02cf
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

It doesn't list a Kernel Driver in Use (like in Count_Alucard) Why so? My sound works well in other operating systems.

---

### Post by Silver Streak on 2009-08-28
> **johnjoy said:**
> I am inside an institute and it has proxy. Can you tell me how to bypass this proxy, and download alsa updates.
I will be thankfull for any help.

John

Add the following line to the beginning of the alsa install script (after the #!/bin/bash part):

```
export http_proxy=url.of.proxy.edutainmentcollege.edu:1234
```

Replace the URL with the URL of the school's proxy, and replace 1234 with the port number (probably 8080). This will not bypass the school proxy, but rather redirect any applications aware of the http_proxy variable (in this case, wget) through the proxy.

Hope this helps!

---

### Post by Whisp3r on 2009-09-06
I had the same problem as count. I upgraded my ASLA to .20, and yet, I still have no sound. 

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Dell Device 02cf
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I checked my mute volume. I've tried installing (successfully) three different ALSA versions. After all this poking and probing, I still have no sound. Extremely frustrating, and a major blow to my belief I should be using Linux as a OS. I've tried this with other distros (live boot cds) and also have no sound. 

Can anyone suggest any other ideas on how to fix this?

---

### Post by Whisp3r on 2009-09-06
I've got it fixed for the most part; I upgraded to ALSA .21 and I have sound again. The only problem I'm having now, which is minimal, but still really annoying, is when I reboot/shutdown, I get a loud feedback type sound from my speaker for a second. I thought it was my pcspkr, but that's still blacklisted. It also did it with my alert sound (IE, backspace when you can't backspace), but I muted that, so that part has been fixed. Any suggestions on how to fix this last remaining feedback noise sound? I disabled the logout sound, but it still does it.

---

### Post by Saint Aardvark on 2009-09-09
> **Pcniatic said:**
> Thanks count_alucard, I did update to alsa runing a modified script available [here]("http://ubuntuforums.org/showpost.php?p=7150907&postcount=161") (I just change the alsa version to 1.0.20) and it did work great  Hi Pcniatic -- thanks very much for this.  This worked perfectly on my wife's laptop, another Inspiron 1440 w/Jaunty.

---

### Post by Whisp3r on 2009-09-09
Hi Saint,
 Congrats on getting your sound to work. Do you have any noise problems while shutting down? What version did you upgrade to?

---

### Post by harsha.angadi on 2009-09-15
[http://ubuntuforums.org/attachment.php?attachmentid=111182&d=1240758387](http://ubuntuforums.org/attachment.php?attachmentid=111182&d=1240758387)
try out this...

---

### Post by Pcniatic on 2009-10-22
To use the new Alsa 1.0.21 driver, I recomend visit [this site]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/") for instructions.

---

