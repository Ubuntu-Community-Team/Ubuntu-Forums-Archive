---
title: "DVD burning problem with Nautilus, Graveman, K3b and Nero Linux. You name it!"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by zodmaner on 2007-05-18
I use Ubuntu 7.04 with ASUS DRW-1608P DVD-recorder and all of my attempt to burn DVD have result in failure. At first I try using Graveman, which end with an error message input/output error. Then I download and try K3b, which also fails. Then I try Nautilus and Nero Linux, both of which fail. 

After this I boot into Windows XP and try to burn the same data on my linux partition using Nero and the same media I use when trying to burn it on Ubuntu, and guess what? It burn successfully without any problem at all. I can even view the DVD in Ubuntu. So it seems that the problem is not with my drive but with Ubuntu.

So anyone know what cause this problem and how to fix it?

---

### Post by zodmaner on 2007-05-18
Ok guys. I manages to get the burn working by enabling the DMA for my drive using this command:

 > sudo hdparm -d 1 /dev/hda

(Thanks goes to K3b for suggesting that I enabling DMA although for a completely unrelated reason :) )

Anyway, if you have problem burning DVD or CD, try enabling DMA. It might help just like it did in my case.

---

### Post by varnav on 2007-07-31
I have exactly the same problem. I will try this solution today to see if it works and report here.

---

### Post by raydar on 2007-07-31
Hi--

I'm running Feisty & had been able to burn DVDs and CDs in my Sony DQ-Q28A drive.  Tried overburning a DVD just a few little megs once, and maybe it was a coincidence, but soon after that I found I could burn only CDs and not DVDs in Linux.  As other threads have reported, I can burn both DVDs and CDs fine in WinXP.

I checked the drive's DMA setting with 

hdparm -d /dev/hdd

and found that it's enabled, but I've tried only Nautilus and Brasero as far as burning apps go.  What happens is the burn process starts in the burning app, but little or no progress is ever shown and after tens of minutes the burn session aborts, spits the disc out, and gives me an error/debugging box. 

See the attached output--hopefully it will better explain what's going on.

Thanks for any help!

--Raydar

---

### Post by kelvin spratt on 2007-07-31
i think you may have some bad code that causing the problem You could try Nero as it does not share resources it will tell you if DMA is turning off or if your writer is not being given exclusive access  ie the disc has unmounted before writing as this sounds like the problem.
i use Brasero and Nero and  have burned 200+ DvDs on Feisty never had a problem  a lot of writers do not like overburning DVD My Plextor will only over Burn DVDR+ in XP  But overburns anything in Linux,

---

### Post by bogolisk on 2007-07-31
[LIST=1]
[*]hal: The stupid HALD is known for interfering with dvd burning (hald-addon-storage pokes the drive every 2 secs).
```

p$ ps -A f | grep hald
31667 pts/1    S+     0:00              \_ grep hald
21333 ?        Ss     0:00 /usr/sbin/hald
21334 ?        S      0:00  \_ hald-runner
21350 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/event1
21351 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/event4
21352 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/event5
21353 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/event6
21360 ?        S      0:00      \_ /usr/lib/hal/hald-addon-cpufreq
21361 ?        S      0:00      \_ hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
21371 ?        S      0:00      \_ hald-addon-storage: polling /dev/hdd (every 2 sec)
21392 ?        S      0:00      \_ hald-addon-storage: polling /dev/sdc (every 2 sec)
21394 ?        S      0:00      \_ hald-addon-storage: polling /dev/sdd (every 2 sec)
21397 ?        S      0:00      \_ hald-addon-storage: polling /dev/sde (every 2 sec)
21404 ?        S      0:00      \_ hald-addon-storage: polling /dev/sdf (every 2 sec)


```
Try
```
sudo /etc/dbus-1/event.d/20hal stop
```
burn dvd
```
sudo /etc/dbus-1/event.d/20hal start
```
[*]CAV drive and feisty kernel: My cav drive would take up to 1:30 min to spin up to 16x. the ATAPI timeout in the kernel is 10sec, way too short. I've had to bump ATAPI timeout to 3 min. But this require recompiling the kernel.
[/LIST]

---

### Post by varnav on 2007-07-31
Thing with DMA didn't work for me. I'm trying to burn 4.3 Gb file and there seems to be a problem with burning files larger than 4 Gb. And no solution yet!

---

### Post by raydar on 2007-07-31
Thanks for such a swift response, guys; I should've written a long time ago.  Discovered Nero's not free, so I tried 

sudo /etc/dbus-1/event.d/20hal stop

first, and I thought it was working as my progress bar hurried right along, but then I realized Nautilus was only creating an image.  I was using one of the previous failed-burn discs (which the Nautilus file browser called "empty"), but I thought maybe it got just enough written to it to ruin it.  But even with a fresh new blank DVD, both Nautilus and Brasero had stopped offering my burner drive as a destination option; it was image-burn only.  So I did 

sudo /etc/dbus-1/event.d/20hal start

and Nautilus, but not Brasero, had resumed recognizing my burner.  Balked at wasting another DVD to see whether just stopping, fooling around, and restarting would fix the problem; is it worth a try?  Do I just need a slightly different command (different dbus number or something)?

---

### Post by bogolisk on 2007-07-31
I've seemed fixed the issue for my machine but I've done many tinkering so I'm not sure which combination was sufficient:
[LIST]
[*]stop hal before burning DVD (even before inserting the disc.) Just killing the appropriate hald-addon-storage that's polling your DVD drive is sufficient. The main problem here is HAL stupid , unaware that the drive is performing a critical task and keep poking at it. From code quality POV, HAL is probably the worse component of the ubuntu desktop.
[*]remove the ata_generic module (i.e: sudo rmod ata_generic). I should probably put it in the blacklist. This really depends on your hw. I have no use for ata_generic (from libata's pata support) and it's interfering with the ide drivers.
[*]modified the kernel to increase ATAPI timeouts. This step is hard to do for many of you. I need this because my LiteOn CAV drive takes a long time to spin up. It usually take 1:30min to get into its cruising speed. The timeout in the kernel 10sec.
[/LIST]

Things seem to be ok **for me** now. I hope they would backport kernel 2.6.22 to feisty. 2.6.20 and 2.6.21 are **known** to have DVD burning problem. I can believe they released 2.6.20 as a production kernel!!!

---

### Post by Irihapeti on 2007-08-01
I've not done any tinkering with the software, but I've noted the following:

I seem to need to format the DVD and do the writing as two different operations, otherwise just about every program turn up an error. I did check DMA and it was already on.

I can't get Brasero to do a multi-session disk on DVD-RW, but it seems to do so quite happily with DVD+RW, which I thought was interesting.

Irihapeti

---

### Post by jackmc on 2007-08-01
stopping HAL let me burn. Is there a way to do it automatically though? It is a bit of a pain... I guess I shouldn't complain, at least I can burn now..

---

### Post by jackmc on 2007-08-02
Ok, this fixed it for me: Let me know if it helps you (post 13)

[http://ubuntuforums.org/showthread.php?p=3119859#post3119859](http://ubuntuforums.org/showthread.php?p=3119859#post3119859)

---

### Post by raydar on 2007-08-02
Hi, Jackmc--

I followed that link and did my best in Brasero to find similar settings to those you mentioned for K3b, but there wasn't an "ignore" speed option or a "disc at once" mode option (that I found, anyway).  So I installed K3b and set the speed to "ignore," but the only write mode option offered was "Automatic," so I still never managed to select disc-at-once.  I left dma alone, i.e., enabled, and also didn't stop hal (bec. last time I did, I was only allowed to create images; my DVD drive was no longer seen/offered).  When I tried to burn a DVD in K3b, I got the same bad behavior as in Brasero & Nautilus (glacial progress and, after a few minutes, everything else ground *almost* to a halt, even mouse movement).  K3b didn't bomb out and give me an error message, though, so I just left for work and let the thing run; it had burned 4MB out of 800-some MB after about 20 minutes.  Don't know what I'll find when I get home.

It's nuts to have to resort to extraordinary measures just to burn a DVD now, after having no trouble at all for many months after I originally installed Ubuntu etc.  I hate the idea of reinstalling the whole OS to fix something like this . . . anyone know a set of packages I could un- and then re-install as something more like major surgery but less than an OS reinstall?  Or any other ideas?

Thanks!

---

### Post by raydar on 2007-10-29
Just checking to see if anyone's found a solution to the "can burn CD, can't burn DVD, but can read both" problem.  

Could there be something with certain drives such as my Sony DQ-Q28A?

I haven't been able to burn DVDs in Linux for months, on several installations (Feisty & Gutsy, Ubuntu, UbuntuStudio, Kubuntu), with the DVD burner as a slave and as a master on primary and secondary IDE. Temp-fixes offered here like stopping hal haven't worked for me, unfortunately, and  I was hoping Gutsy would fix it, but no.  

This kind of issue seems to be mentioned relatively often in the forums here.  Please someone tell me it's been fixed and I just haven't found the thread?

One idea:  Earlier in the thread, Kelvin mentioned Nero as something that doesn't share resources with the other apps like k3b & Brasero; if I'm interpreting that right, that means it might use different code that isn't susceptible to or doesn't provoke the same error.  Is there a command-line burning app I could try that does likewise, but that is free unlike Nero?

---

### Post by orthopteroid on 2007-11-20
Hi all,

Originally, I had ubuntu 6.04 on my machine and was able to burn dvds (I think there was all kinds of scsi-ide related nonsense I had to go through, I can't remember). When I upgraded to 7.04 and applied subsequent upgraded packages I lost the ability to burn dvds (even after some udev sg? device permissions tweaking). After a clean install of 7.10 and subsequent upgraded packages (to date) I still can't burn a dvd.

Sometime after my 7.04 upgrade my Pioneer DVR-A09 went kaput. I replaced it the other day with a poineer DVR-112D in a USB2 enclosure and have been test burning a 1.9 GB iso using nero 3.0.2.1 to try to get myself back-uppable again. I believe you can install this version of nero with the demo license on a live cd version of ubuntu for free until 1/1/2008.

Here is what I've found:

- burns and verifies with ubuntu live cd 7.04
- burns but doesn't verify with ubuntu live cd 7.10

So, this suggests to me that some package update since the 7.04 livecd broke it for me (I've got 7 dvd+-R coasters to enjoy now). If I get it working I'll post, in the meantime ... any suggestions?

---

### Post by gregwbush on 2007-11-24
I got my burner to work finally today (was failing every time)... thought i'd sign up, do a search for threads like this and try to help out... there's gotta be people with this issue.

you may already know about checking your drivies **dma** status

```

hdparm -d /dev/hdc

``````

greg@greg-desktop:~$ hdparm -d /dev/hdc

/dev/hdc:
 using_dma     =  1 (on)

```but it goes deeper than this. Well it did for me. In BIOS i see my IDE DVD-RAM drive is configured as **udma2** (66) as it should be.

When i typed this...
```
 hdparm -i /dev/hdc
``````
greg@greg-desktop:~$ hdparm -i /dev/hdc

/dev/hdc:

 Model=HL-DT-ST DVDRAM GSA-H42N, FwRev=RL00, SerialNo=K7571NL4344
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 **UDMA modes: udma0 udma1 udma2 udma3 *udma4** 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

**  * signifies the current active mode**
```... I see ubuntu has incorrectly detected the dma mode and set it to **udma4** (asus A8N anybody?)

To set it correctly run
```
sudo hdparm -X udma2 -d1 /dev/hdc
``````
greg@greg-desktop:~$ sudo hdparm -X udma2 -d1 /dev/hdc
[sudo] password for greg:

/dev/hdc:
 setting using_dma to 1 (on)
 setting xfermode to 66 (UltraDMA mode2)
 using_dma     =  1 (on)
```and try it out!
The hdparm -X option is described as (DANGEROUS) in the command's help thingy... so i guess you wanna make sure you set to the correct dma mode. Then again mine was set wrong to begin with and all is well, it's probably more dangerous to mess with your hard drive settings, though to be honest i don't really know.

Anyway if that was your issue and these steps worked like it did for me... you'll need to make it happen automatically when you boot up. There's a file called hdparm.conf in /etc that you need to edit. I use gnome editor "gedit". You'll want super user access so...

```
sudo gedit /etc/hdparm.conf
```Scroll all the way down to the bottom and add the following lines

```

command_line {
hdparm -X udma2 -d1 /dev/hdc
}
```... save and you should be good to go ;)

---

### Post by raydar on 2007-12-01
Wow, I can't believe it!  I've burned two DVDs!  I wish I could say "problem solved," but I'm doing a happy-dance anyway 'cause this is the first thing that's worked in many months--thank you, gregwbush!

[COLOR="Sienna"][LEFT]sudo hdparm -i /dev/hdd[/LEFT][/COLOR]

gave me

[COLOR="Sienna"][LEFT] /dev/hdd:

Model=SONY DVD RW DW-Q28A, FwRev=KYS1, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode
[/LEFT]
[/COLOR]
and then

[COLOR="Sienna"][LEFT]sudo hdparm -X udma2 -d1 /dev/hdd[/LEFT][/COLOR]

gave me

[COLOR="Sienna"][LEFT]/dev/hdd:
 setting using_dma to 1 (on)
 setting xfermode to 66 (UltraDMA mode2)
 using_dma     =  1 (on)[/LEFT]
[/COLOR]
at which point I went and found an .iso to burn.  I opened the UbuntuStudio 7.10 image I had lying around with Brasero, and voila, it burned it lickety split instead of bogging down the system and taking hours to do nothing.  The DVD I burned subsequently failed a consistency check, but again, I haven't been able to burn *any* DVD successfully.

BUT then I tried just a regular data-DVD session in Brasero, i.e., copying some 900MB of files to a DVD instead of burning an image.  Brasero bogged down and the burn never really got started, just like before, and I had to power off the machine just to recover (merely restarting or resetting doesn't convince  the DVD drive to  stop attempting the burn).

After powering back on, I found a different .iso to burn, this one an image I'd created of a DVD of about a GB worth of image files.  Rather than use Brasero, I just right-clicked on the file and chose Open, the "Write to Disc" dialog appeared, and I clicked "Write."  This image burned fine too--there wasn't an option for a consistency check, but I was able to browse the DVD & view the picture files on it.

Obviously the udma setting had a direct role in why I couldn't burn DVDs at all (notwithstanding being able to burn CDs); but I didn't see this new hitch coming:  Why can I now burn DVD images but not data DVDs?

---

### Post by siddeek on 2007-12-05
hello dear 
 i followed following code

```
sudo hdparm -d1 /dev/sda 
```

but it has given following massage


```
setting using-dma to 1(on)
          HDIO-SET_DMA failed;  inappropriate ioctl for device
```

still i am not able to burn dvd,
          ple help me

---

### Post by jtothar on 2007-12-06
SERIOUSLY! Can anyone tell me why linux is unable to burn cheap media but windows can do it all day with the same hardware? Im sick and tired of k3b being worthless all the while windows could burn the exact same media in the same burner. "the burner doesnt like the media" ********!

---

### Post by shad0w_walker on 2007-12-06
> **jtothar said:**
> SERIOUSLY! Can anyone tell me why linux is unable to burn cheap media but windows can do it all day with the same hardware? Im sick and tired of k3b being worthless all the while windows could burn the exact same media in the same burner. "the burner doesnt like the media" ********!

If I had to take at a guess its probably some odd configuration issue. I have never encountered any CD/DVD burning issues in Linux and the odds that Linux is just 'unable' to write to your choice of cheap disc is practically 0.

---

### Post by GreenMeanie on 2007-12-07
I am getting updates daily and you or going to tell me they can't fix this problem yet?

---

