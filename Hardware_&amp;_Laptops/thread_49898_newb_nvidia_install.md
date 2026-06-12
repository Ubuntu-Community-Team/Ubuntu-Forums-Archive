---
title: "newb nvidia install"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by CraigRR on 2005-07-18
Hi folks I'm new to linux (1 day) and new here so bear with me.

Last night I installed  :grin:  ubuntu on a machine with the following specs-

Athlon 800MHz
512MB SDRAM
30GB HD [15GB NTFS partition with XP Pro] [15GB formatted by ubuntu, for ubuntu]
Geforce MX440 [stuck in AGP 1x due to mobo limitations]
Hercules MuseLT PCI soundcard
Linksys network PCI card
MS mouse
generic keyboard

The install went fine [dual boot fine], I can access the internet via my zyxel router, so the network card is working fine. 

The soundcard is listed as a C-media device [though its officially Hercules], and though I havent hooked up any speakers yet I dont think sound wil be a problem, as in Windows, C-Media is listed in the optional software updates via windows update.

My main stumbling block seems to be nvidia. 

The display is obviously working, but lacking decent 3D performance [even though the MX440 is a glorified GF2]. I havent attempted to install any nvidia drivers yet.

I've browsed this site till I'm blue in the face and the amount of nvidia problems\info frankly boggles me  :| 

From what I've gathered, just clicking on the nvidia driver after downloading it like I would on a windows .exe is a bad idea?

Unfortunately, thats the ony way I know how to install a driver.

When I start reading some of the more complex methods [to me anyway] to install  I get boggled when I see people say they typed /xxx into a command line etc. [which incidentally where is the command line thing I see people to refer in ubuntu?]

[edit]eg [[color=blue]this brief install instructions[/color]](https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28nvidia%29) I cant make head nor tail of, if this is correct and the safest way for me to install, where do i start.[/edit]

So as a total Linux novice, what do I do to install nvidia drivers on my machine as safely as possible?

Thx for any help
 :?

---

### Post by netrattler on 2005-07-18
Just add the extra repositories, then click on Applications -> System Tools -> Terminal -> and copy and paste from the Nvidia howto.

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

Joe

---

### Post by CraigRR on 2005-07-18
Thx for the reply,

After a few attempts due to the odd spelling error etc  ;-)  it seems to be working.

Looking in Applications > System Tools > NVIDIA Settings confirms the GF4MX440 etc

Though, it states the driver version as 1.0-7174. When I was messing around earlier, I downloaded the newest drivers [7667]. 

Is there an easy way to update to this version? 

Incidentally, I downloaded the  NVIDIA-Linux-x86-1.0-7667-pkg#.run file to /home/myname/my downloads, and when I try and find it from the console[terminal?] it keeps saying directory, file not found etc when I know I'm entering the right location. What am I doing wrong?

[edit]
hmm for some reason, now when I reboot the machine, and choose ubuntu off the GRUB menu, instead of taking me to the desktop login screens, it takes me to the command line login [enclosed pic]. I can login and then type /etc/init.d/gdm start and it goes to the desktop. But I have to do that each time I boot\reboot. How do I make it always do this? Like it did before the nvidia install.

Enclosed 2 jpegs, the colourful ubuntu log in screen was how it was prior to nvida install. The other is how it now appears after the nvidia install when it loads ubuntu, here I have to log in, then enter /etc/init.d.gdm start, to get the colourful screen.
[/edit]

Thx again
 :smile:

---

### Post by netrattler on 2005-07-18
See if this corrects your problem when your system boots up start gdm back up and click on System -> Administration -> Synaptic Package Manager. Then click on the Search button and type gdm right click on gdm and click reinstall. Then click the Apply button. Then reboot your computer and see if this corrects it.

As for you problem with "/home/myname/my downloads" If you click on Place -> Home Folder -> rename my downloads to my_downloads linux doesn't like spaces in filenames. Then at the terminal you should be able to go to that directory by using the cd command now. If you really want to keep it like that you can type 
cd /home/username/my\ downloads

Joe

---

### Post by CraigRR on 2005-07-19
> See if this corrects your problem when your system boots up start gdm back up and click on System -> Administration -> Synaptic Package Manager. Then click on the Search button and type gdm right click on gdm and click reinstall. Then click the Apply button. Then reboot your computer and see if this corrects it.


It made no difference  :| , booting up still takes me to the command line login, where I still have to manually enter /etc/init.d/gdm start.

Thx

---

### Post by Lord Illidan on 2005-07-19
Type in :

sudo vi /etc/X11/xorg.conf

And take out the Load "dri" in the modules section

example..

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "dri"                -------------take out this---------------
        Load    "glx"
        Load    "int10"
        Load    "record"

---

### Post by CraigRR on 2005-07-19
I typed sudo vi /etc/X11/xorg.conf

However there are only 2 things listed in the modules section:

Section "Module"
             Load      "bitmap"
             Load      "dbe"

Any other ideas?

Thx
:|

---

### Post by Lord Illidan on 2005-07-19
type in Load "glx"

---

### Post by CraigRR on 2005-07-19
Wait,

 :razz: 

my bad.

When I opened that file before, the scroll bar was full up, indicating there were no further entries (load "dbe" was at the bottom of the page when it first opened).

I just reopened it to add the glx line you mentioned, so I used the cursor keys to scroll down to the modules section.

Lo & behold it scrolled down even further, even though the scroll bar is full.  :roll: 

Here is the full list:

Load     "bitmap"
Load     "dbe"
Load     "ddc"
Load     "dri"
Load     "extmod"
Load     "freetype"
Load     "glx"
Load     "int10"
Load     "record"
Load     "type1"
Load     "vbe"

So I went to do the first thing you said - remove "dri", but when I move the cursor down to that line, pressing backspace doesnt work, pressing delete removes it, but how do I save the changes?

I used the delete key, removed that line, closed it, when I reopened its back there.

Thx
 :)

---

### Post by CraigRR on 2005-07-19
I managed to delete the line now, not quite sure how, but its done.

Cannot find anyway to save the changes though, to be able to reboot and see if it works.

Thx

---

### Post by pailhead on 2005-07-19
[QUOTE=CraigRR]I managed to delete the line now, not quite sure how, but its done.

Cannot find anyway to save the changes though, to be able to reboot and see if it works.

Thx[/QUOTE]

That's why I don't use vi it's too confusing.. use sudo nano /etc/X11/xorg.conf  

nano is much more user friendly..

---

### Post by CraigRR on 2005-07-19
Well alas, using nano enabled me to easily save the file, without the line Load "dri".

But it still boots me to the command line login screen.

Back to square one  :-| 

Thx

---

### Post by JayCnrs on 2005-07-19
If you go to :

/etc/rc2.d 

Do you have a line that says something along the lines SXXgdm?

If this isn't there you need to create the symbolic link to the gdm init script use:

**sudo ln -s /etc/init.d/gdm S99gdm**

---

### Post by CraigRR on 2005-07-19
Typing /etc/rc2.d reveals:

/etc/rc2.d: is a directory

I have no idea how to display the bit you want to look if it contains SXXgdm.

According to "search for files" there is no files of that name found

Thx

---

### Post by CraigRR on 2005-07-19
Yes its in there: s13gdm modified 23/03/05

I'm getting somewhat  :neutral: disheartened now, so I typed in what you said anyway. Rebooted, still the same.

Thx

---

### Post by JayCnrs on 2005-07-19
I'm just wondering if you press the ESC key at the Grub prompt make sure it is selecting the regular kernal and not the Recovery Mode.  

Also at the prompt try:

**sudo dpkg-reconfigure gdm** 


Now if it still isn't working take a look in /etc/inittab, make sure the following line reads:

```
# The default runlevel.
id:2:initdefault:
``` 

Let us know how the battle goes

---

### Post by CraigRR on 2005-07-21
Definetly selecting the regular kernel at GRUB.

Typed sudo dpkg-reconfigure gdm, rebooted.

No change.

>  The default runlevel.
id:2:initdefault:
yes, this is present in inittab.

 :-|

---

### Post by CraigRR on 2005-07-27
Decided to give up, reinstall OS, minus ubuntu.

Things like this put me right off  :-P 

Thx anyway one and all.

---

