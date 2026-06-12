---
title: "Plugging in headphones doesn't mute laptop speakers"
date: 2011-02-16
forum: Hardware
---

### Post by TheUnwiseman on 2011-02-16
I'm mostly creating this thread for lidex, because I've already PMed him asking the question, but he asked me to make a public thread to answer the problem, so here it goes.

I've got an ASUS X52J laptop with Conexant 5069 codec sound card. My problem is that the laptop speakers don't mute when I put my headphones in. I've already upgraded to the newest version of ALSA (1.0.23).

This is the link to my alsa-info.sh output:

[http://www.alsa-project.org/db/?f=997cd30a55d90cfd55ec98029257aa5047fd1662]("http://www.alsa-project.org/db/?f=997cd30a55d90cfd55ec98029257aa5047fd1662")

Thanks for the help in advance.

---

### Post by lidex on 2011-02-17
How did you update to 1.0.23?
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by TheUnwiseman on 2011-02-17
That worked!

To answer your question, I updated to 1.0.23 by building it from tarballs.  I forget where I put the link to the site that walked me through it.

Thank you very much, lidex!

---

### Post by lidex on 2011-02-17
And you're welcome!



k &#8800; x

---

### Post by TheUnwiseman on 2011-02-17
Oops, sorry. :X

*lidex

Edit: Fixed the k->x in other posts now. :P

---

### Post by treepete on 2011-09-14
hi...
for the record; i have a lenovo g470 running ubuntu 10.10 and this worked for me. 
thank you

---

### Post by www.rzr.online.fr on 2011-10-12
> **treepete said:**
> hi...
for the record; i have a lenovo g470 running ubuntu 10.10 and this worked for me. 
thank you



does the mic also work on g470 ?

-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

### Post by treepete on 2011-12-05
sorry to be tardy..
yes, the mic also works, though it has some static.
v

---

### Post by thelastspud on 2011-12-06
I get up to step two but I get these two errors 
```

bradley@bradley-K52Je:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
[sudo] password for bradley: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-alsa-driver-modules-2.6.35-31-generic-pae
E: Couldn't find any package by regex 'linux-alsa-driver-modules-2.6.35-31-generic-pae'
bradley@bradley-K52Je:~$ 

```

---

### Post by lidex on 2011-12-27
> **thelastspud said:**
> I get up to step two but I get these two errors 
```

bradley@bradley-K52Je:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
[sudo] password for bradley: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-alsa-driver-modules-2.6.35-31-generic-pae
E: Couldn't find any package by regex 'linux-alsa-driver-modules-2.6.35-31-generic-pae'
bradley@bradley-K52Je:~$ 

```

It's not available for that kernel. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by gmangalo on 2012-01-03
hi lidex,

i encountered the same error with thelastspud, followed your comments and get 

Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : y
Uploading information to [www.alsa-project.org]("http://www.alsa-project.org") ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=a6653a1c99849d74d548d873e221891eca866ba9](http://www.alsa-project.org/db/?f=a6653a1c99849d74d548d873e221891eca866ba9)

Please inform the person helping you.

What should I do next? By the way I have ASUS K52J series running in Ubuntu 10.10


Thanks in advance

---

### Post by lidex on 2012-01-03
> **gmangalo said:**
> hi lidex,

i encountered the same error with thelastspud, followed your comments and get 

Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : y
Uploading information to [www.alsa-project.org]("http://www.alsa-project.org") ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=a6653a1c99849d74d548d873e221891eca866ba9](http://www.alsa-project.org/db/?f=a6653a1c99849d74d548d873e221891eca866ba9)

Please inform the person helping you.

What should I do next? By the way I have ASUS K52J series running in Ubuntu 10.10


Thanks in advance

Try editing your alsa-base.conf:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Change this line:
```
options and-hda-intel model=k52j position_fix=1
```
to this:
```
options snd-hda-intel model=hp-laptop
```
Save. Close. Reboot.

---

### Post by gmangalo on 2012-01-03
hi lidex,

thanks!!! works like gem!

---

### Post by D3C3PT1ON on 2012-01-18
> **lidex said:**
> It's not available for that kernel. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.

when i ran the script it seem i never got a upload back this is what i got back.
some information i have is I'm using a thinkpad x120e with ubuntu 10.10


> --2012-01-18 07:39:52--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org]("http://www.alsa-project.org")... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80]("http://www.alsa-project.org%7C77.48.224.243%7C:80")... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2012-01-18 07:39:54--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80]("http://www.alsa-project.org:80").
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [   <=>                                 ] 27,247      27.4K/s   in 1.0s    

2012-01-18 07:39:56 (27.4 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

alsa-info.sh: line 42: ping: command not found

An error occurred while contacting the [www.alsa-project.org]("http://www.alsa-project.org").
Your information was NOT automatically uploaded.

Your ALSA information is in /tmp/alsa-info.txt.mp0SrX3DfG


---

### Post by troelsjc on 2012-03-30
Hi, I got the same problem,
the output from the script is here:
```
http://www.alsa-project.org/db/?f=d17c142cca0f7f0232830e561a8d3e497741b057

```

As far as I understood. the problem is that there is no alsa driver for the kernel version I am using:
```

angelo@angelo-K50AF:~$ uname -r
3.0.0-17-generic
```

Following the instructions from lidex:
> **lidex said:**
> Try editing your alsa-base.conf:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Change this line:
```
options and-hda-intel model=k52j position_fix=1
```
to this:
```
options snd-hda-intel model=hp-laptop
```
Save. Close. Reboot.

I guess editing the alsa-base.conf can resolve this problem, changing the line to something like this, as my computer is an ASUS:
```
options snd-hda-intel model=asus-laptop
```

Is this the right way to risolve the problem?

---

### Post by Yellow Pasque on 2012-03-30
'asus-laptop' is not a valid keyword. YOu have a VIA VT1708 codec, and a lot of jack sensing issues are resolved with ALSA 1.0.25, so try the latest driver:

```
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install alsa-hda-dkms
```

---

### Post by Ynothna on 2012-04-05
> **Temüjin said:**
> 'asus-laptop' is not a valid keyword. YOu have a VIA VT1708 codec, and a lot of jack sensing issues are resolved with ALSA 1.0.25, so try the latest driver:

```
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install alsa-hda-dkms
```


I was having the same problem (Ubuntu 10.10) and the above fixed it for me.

Thanks very much!

---

