---
title: "Power Management for Acer Aspire 5050"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by mikegu on 2007-08-22
I have an Acer Aspire 5050 (Turion 64 2200+)  and I can't get power management to work.  Ubuntu never sees that I'm on battery.  Any fixes?

---

### Post by nosrednaekim on 2007-08-22
I have the same laptop. except with a tuion x2. No problems on Kubuntu 7.04

When on battery please run "cat /proc/acpi/battery/BAT1/state" and paste the output.

---

### Post by mikegu on 2007-08-23
present:                 no

---

### Post by mikegu on 2007-08-25
Ran the "cat /proc/acpi/battery/BAT1/state" and got the following results:

present: no

---

### Post by nosrednaekim on 2007-08-25
VERY odd..

I get the following

```

[geebee:michael]~> cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      3670 mAh
present voltage:         12382 mV

```

try running "hal-find-by-capability --capability battery"

---

### Post by mikegu on 2007-08-26
Here's the results.

root@dadderlx:/home/dadder# hal-find-by-capability --capability battery
/org/freedesktop/Hal/devices/acpi_BAT1

---

### Post by nosrednaekim on 2007-08-26
wow... thats odd. Umm I really don't know what the problem is, probably something wrong with ACPI. 

Try turning off the computer, and taking out the battery for like 5 minutes to reset all the BIOS functions, etc.

---

### Post by yakolev on 2007-08-26
I have the same model and every step described here is duplicated on mine. I've also had to fight to get sound/wifi up right but (thanks to the efforts of bmartin) am now operational on both counts.

I also have an issue with logout, for when I log out of gnome gdm hangs seemingly indefinitely and I have to hard-off the machine.

The ACPI simply doesn't seem to be functional.
I've tried this with .20-16 and the gutsy kernel and love just doesn't seem to be in the air...

---

### Post by nosrednaekim on 2007-08-26
hmmmm thats odd. Maybe my 5050 is a bit older model as I got it in October of 2006.

It has a Atheros 5005G (working by default in gutsy)
Turion X2 TL-52
ATI HDA audio (working with a patch in fiesty, and by default in gutsy)

Power management also works perfectly with suspend and battery stuff. 

So whats the hardware in yours? I know there was a 5050 model with broadcom...

---

### Post by yakolev on 2007-08-27
hmm... I've got a similar setup but the wireless didn't take with gutsy so still using ndiswrapper. Sound I haven't fully experimented with on that kernel but did also work in gutsy (though not flawlessy, it broke the control keys and didn't pick up all the channels it should have. I had, however, recompiled ALSA beforehand and had similar issues)

In all of this I haven't checked the other ACPI functions like suspend so I'll try that now...
ETA: Yup suspend is fine, it's really just the battery issue. The only other thing that doesn't work is the card reader but I heard that one is fine in 2.6.23 so I'll just wait on that.

---

### Post by nosrednaekim on 2007-08-27
hmm you are right.. not all the channels are there.

for how to fix the sound in fiesty without recompiling: 
[http://nosrednaekim.wordpress.com/tag/computer-hardware/acer-aspire-5050](http://nosrednaekim.wordpress.com/tag/computer-hardware/acer-aspire-5050)

Oddly enough, the card reader workes in suse 10.1.... however, other things did not.

---

### Post by yakolev on 2007-08-27
Ah! Thank you your website is quite helpful.
As stated, methinks I'll just wait on the card-reader since I've got a few external ones already. I could patch the kernel but I really don't feel like maintaining my own fglrx compilation with every kernel update so I'll just wait until gutsy goes up to 2.6.23.

---

### Post by robertor on 2007-08-28
Hi!
I recently got the acer 5050 and i have the same problem with the battery. A friend has the same notebook, but the diference between his notebook and mine is a number after 5050 in the adhesive that is under the keyboard. My sticker said Aspire 5050-4835 and my friend say 5050-3007 think so. The subject is he don´t have problems with battery. He and me are trying ubuntu feisty.
I suspect that it could be differences in the bios, my bios is 3009, but i don´t know what version has him.
What about you? What version do you have? What will happen if i make a downgrade in the version of the bios?
Greets a lot!
Roberto

PD: sorry for my english.

---

### Post by nosrednaekim on 2007-08-28
I have BIOS version 3109  (the "Vista" bios"). My REAL model # is 5050-5410 I also have the dual core Turion, do all of you have the single core one?

---

### Post by yakolev on 2007-08-28
This one is indeed a single core

---

### Post by eddiemcm on 2007-08-30
I have not had much luck with my acer laptop either. I wanted to put the 64 bit version on but it would not work, so i installed 32 instead. Then had problems with sound and found that it was just the surround in the volume was muted. I still can not get my wireless to work, so i have to resort to using vista at school. The power management does not seem to work on mine either. I have a 5050-3785, with atheros ar5bxb63, which shows up as 5007 for windows drivers, i have tried using ndiswrapper, and mad wifi. I also can not get the advanced graphics working, I have an ATI radeon xpress 1100. any help would be great.

---

### Post by hashimoto on 2007-08-30
I have an old Compaq Presario 1201EA and seem to have a similar problem with the battery. It is recognized but the capacity "current rate" is not "known" to my Ubuntu, hence it will run on battery until sudden death.

My cat gives:

cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      0 mAh
present voltage:         16800 mV

cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         4400 mAh
last full capacity:      0 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  4 mAh
capacity granularity 2:  4 mAh
model number:            4400
serial number:           00020023
battery type:            LION
OEM info:                 COMPAQ 

hal-find-by-capability --capability battery
/org/freedesktop/Hal/devices/acpi_BAT1

Changing from battery to AC and back is OK, battery voltage is correctly read, so it seems that the charge rate is the only thing not recognized. As this laptop is a very old I suspect that the bios does not correctly support acpi. Could the apm work better?

---

### Post by RageOfOrder on 2007-08-30
I had a similar problem with Slackware 12 on my Acer 9410. 

Here's a solution to try.

Pass the paramater "apm=off" to your kernel.
If you use grub, edit your /boot/grub/grub.conf (or menu.1st, whichever exists)
and look for the line that starts with "kernel"
Just tack "apm=off" to the end of that line (without quotes"

That will disable APM from loading and if ACPI is compiled into your kernel, it will be used now instead. It's also possible that your kernel has ACPI compiled as modules, in which case you should try loading them as such:

```

sudo modprobe acpi
sudo modprobe battery
sudo modprobe ac
sudo modprobe button

```

Once those are loaded, it should pick up your battery just fine.

If that works, you can add enter these commands and they will load when you boot.

```

sudo echo "acpi" >> /etc/modules.autoload.d/kernel-2.6
sudo echo "battery" >> /etc/modules.autoload.d/kernel-2.6
sudo echo "button" >> /etc/modules.autoload.d/kernel-2.6
sudo echo "ac" >> /etc/modules.autoload.d/kernel-2.6

```

Edit: two spelling mistakes in code

---

### Post by lioninthesky on 2007-08-30
I've been having an interesting journey myself with regard to this.  I'm using an ACER 5050 series.  I have noticed something, however, and I'm not sure if this is an issue or not - lsmod shows aus_acpi to be the active acpi module.  My battery status will not change, it simply states 'on AC power' and N/A for options.  After trying all solutions previously stated in this thread, all three files in /proc/acpi/battery/BAT1 state "no" instead of hardware related output.  No apm functions work as they are not supported in my kernel build, I didn't think this would be related to ACPI but I figured it might be worth mentioning.

On a side note, got wireless working without a problem using this thread: [http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

---

### Post by lioninthesky on 2007-08-30
> **lioninthesky said:**
> I've been having an interesting journey myself with regard to this.  I'm using an ACER 5050 series.  I have noticed something, however, and I'm not sure if this is an issue or not - lsmod shows aus_acpi to be the active acpi module.  My battery status will not change, it simply states 'on AC power' and N/A for options.  After trying all solutions previously stated in this thread, all three files in /proc/acpi/battery/BAT1 state "no" instead of hardware related output.  No apm functions work as they are not supported in my kernel build, I didn't think this would be related to ACPI but I figured it might be worth mentioning.

On a side note, got wireless working without a problem using this thread: [http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

Correction: lsmod shows asus_acpi, not aus_acpi

---

### Post by robertor on 2007-08-30
> **nosrednaekim said:**
> I have BIOS version 3109  (the "Vista" bios"). My REAL model # is 5050-5410 I also have the dual core Turion, do all of you have the single core one?


Well, my turion is a single core. I was thinking that it could be the bios version the problem, so if you have the same version....
May the cpu do the diference? What other thing it could be? I´mrunning feisty, what are you running nosrednaekim?
Thanks!
Roberto

---

### Post by nosrednaekim on 2007-09-01
I'm running fiesty and gutsy, both of which work just fine.

and how do you see what the active ACPI module is? I know I have asus_acpi loaded, but i'm not sure if its the active one.

---

### Post by robertor on 2007-09-01
Well, I do a ```
roberto@pitufo:~$ lsmod |grep acpi
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi

```
And there i can see an acpi module loaded. When i do a modprobe acpi i got an error:
```
root@pitufo:~# modprobe acpi
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): Device or resource busy
```

By the way, i got a combination that allow use the wifi without problem.  The original situation was a kernel panic that i got in the boot. If i turn off from the switch in front of laptop i could boot without problem, but when i activate again the wifi from th switch the laptop freeze. The solution for me was put a acpi=nopci in the option in grub. With this i could use the option of suspend.
Now im suspecting that may be a combination of acpi option that it could allow me use the acpi funcion to know the state of my batt. Do you know another options?

Greets!
Roberto

---

### Post by nosrednaekim on 2007-09-01
no, I don't. 

And I don't have a clue what you guy's problem is. I'm sorry. Wish I could help

---

### Post by lioninthesky on 2007-09-03
> **robertor said:**
> Well, I do a ```
roberto@pitufo:~$ lsmod |grep acpi
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi

```
And there i can see an acpi module loaded. When i do a modprobe acpi i got an error:
```
root@pitufo:~# modprobe acpi
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): Device or resource busy
```

By the way, i got a combination that allow use the wifi without problem.  The original situation was a kernel panic that i got in the boot. If i turn off from the switch in front of laptop i could boot without problem, but when i activate again the wifi from th switch the laptop freeze. The solution for me was put a acpi=nopci in the option in grub. With this i could use the option of suspend.
Now im suspecting that may be a combination of acpi option that it could allow me use the acpi funcion to know the state of my batt. Do you know another options?

Greets!
Roberto

That's the output I received from lsmod, and the error message from modprobe/insmod.  I had to custom compile the module. I'm assuming anyone here who has been using the acer_apci module got it from this location:  [http://code.google.com/p/aceracpi/]("http://code.google.com/p/aceracpi/").  If so, I'll try and recompile it and work with it some more.  There's got to be something I'm missing.  It does say, after all, that it is supposed to work with the 5050 series: [http://code.google.com/p/aceracpi/wiki/SupportedHardware]("http://code.google.com/p/aceracpi/wiki/SupportedHardware")

---

### Post by nosrednaekim on 2007-09-03
I'm not using the acer_acpi driver,  But tell me if that works...

---

### Post by robertor on 2007-09-03
> **lioninthesky said:**
> That's the output I received from lsmod, and the error message from modprobe/insmod.  I had to custom compile the module. I'm assuming anyone here who has been using the acer_apci module got it from this location:  [http://code.google.com/p/aceracpi/]("http://code.google.com/p/aceracpi/").  If so, I'll try and recompile it and work with it some more.  There's got to be something I'm missing.  It does say, after all, that it is supposed to work with the 5050 series: [http://code.google.com/p/aceracpi/wiki/SupportedHardware]("http://code.google.com/p/aceracpi/wiki/SupportedHardware")

At this moment im not using acer_acpi module. And i dont´t get a useful function loading this module. In acpi directory i get this.
```
root@pitufo:/proc/acpi/acer# ls
bluetooth  brightness  interface  version  wireless
```

Roberto

---

### Post by robertor on 2007-09-04
Well i hace solved my problems. I did a dowgrade of my bios. I was using 1.3309 and i install a 1.3302 and now i don´t have any more problems with the battery.
Greets!
Roberto

---

### Post by maksei on 2007-09-06
Thanks robertor - 
I've downgraded my Phoenix bios from 1.3309 to 1.3303 (sic!) which can be obtained from Acer Europe here:
[ftp://ftp.work.acer-euro.com/notebook/aspire_5050/bios/3303.zip](ftp://ftp.work.acer-euro.com/notebook/aspire_5050/bios/3303.zip)
 
Now I no longer have to boot with the acpi=off or acpi=ht cheat code.
Also I don't have to power off the laptop manually now.

thanks folks

---

### Post by helwitch on 2007-09-06
Anyone know a way to get powermanagement on the 5050-3785 working without downgrading the BIOS? And, if I've got everything (sound, wireless) working on the current BIOS, and I downgrade the BIOS, is it likely to break things? as much effort as it took me to get the wifi working, I really don't want it getting broken. But I'd also like to have some tiny little clue how much battery life I've got left at any given time.

---

### Post by maksei on 2007-09-08
i got alsa and wifi (via ndiswrapper) working before downgrading the bios, which mind you hasn't broken anything as far as i can see. my model # is acer aspire 5050-4570 though.
for the record, i'm running debian etch with kernel 2.6.18

---

### Post by lioninthesky on 2007-09-09
I'm going to try downgrading the BIOS to see if that resolves the issue.  I have noticed that although I can shut down the laptop fine, if I log out of an account (hoping to go back to the login manager) all I get is a black screen and no response from the laptop.  The only option I am left with is to hard shutdown the laptop via power button.

Has anyone else had a problem logging out (not shutting down/suspending/hibernating) and not getting back to the login manager?

I'm suspecting it's related to the power/acpi issue.  I'll be looking through the logs shortly, but I thought I would ask to see if anyone has experienced this.

---

### Post by lioninthesky on 2007-09-09
> **nosrednaekim said:**
> I'm not using the acer_acpi driver,  But tell me if that works...

From my recent experience, the module did not appear to solve any of the issues I have had with the laptop.  Although, it is being used so I'm hesitant to say it's not providing any benefit.

---

### Post by yakolev on 2007-09-11
The issue with the black screen logout is common to the video card and a solution is to go to the login options and tick the box for "restart the x server with each login"

I'm considering a bios downgrade but not sure how to go about it, seeing as how it is intended to be done from windows and I'm not particularly enamored with reinstalling vista solely for a bios operation...

---

### Post by robertor on 2007-09-11
> **yakolev said:**
> The issue with the black screen logout is common to the video card and a solution is to go to the login options and tick the box for "restart the x server with each login"

I'm considering a bios downgrade but not sure how to go about it, seeing as how it is intended to be done from windows and I'm not particularly enamored with reinstalling vista solely for a bios operation...

The biot that i installed (1.3302) it was labeled like vista bios. I´m having problem wih this bios. The computer randomly it doesnt boot and the error is a "Bug soft detected". A friend has the same computer but with 1.3303 bios and he doesnt have problem. Im gonna try when i could have time.
Greets!
Roberto

---

### Post by nosrednaekim on 2007-09-11
Indeed I get that error... but I think its a HW problem. I only get it when I take it away from the AC adaptor and carry it around (maybe a bad ground or something)

@yaloklev
And thats why I don't erase windows. I think you can load the biod off a floppy. Of course then you need a USB floppy drive

---

### Post by yakolev on 2007-09-12
Ah k, well I do know that one can do a bootable cd using an image intended for a floppy so I might try that.  I'll need a dos flashing program though which can be rather suspect....

---

### Post by robertor on 2007-09-13
> **nosrednaekim said:**
> Indeed I get that error... but I think its a HW problem. I only get it when I take it away from the AC adaptor and carry it around (maybe a bad ground or something)


At least! I solved all problem that i have had with this notebook. The soft bug detected i solved. I uninstall ndiswrapper package provided by ubuntu, i donwloaded the source form [http://ndiswrapper.sf.net](http://ndiswrapper.sf.net) and automagicamente all my problems disappear.

After the change of my bios i began to get the status of my battery but sometimes all this information was nasty, ie. it was unplugged from AC and it said that was conected and charging and the battery go discharging very very fast. Other problem taht i was getting was the lost control of the keyboard... this don´t response. All this thing where very very nasty experience using the notebook.

Well, after compiling ndiswrapper all work very nice. The battery  work very good, i don´t have random problems booting. I can activate/desactivate the wireless frome the switch (no led yet) and don´t freeze (sometime i got a kernel panic). I have had to add irqlpool to the grub, because in the first boot after install ndiswrapper it sugeested.

Now, the only thing taht is not working is the webcam and the card reader (this i have not tried anything), but all essential is working.
By the way, have probed an ati drivers and works very very nice... like my old nvidia desktop´s card. A friend probe the last driver recently released today and it goes too much better than me in an older card.
Hopefully all this it is useful for someone else. I thnk that i´m gonna write a how to for this notebook.
Greets!
Roberto

PD: sorry for my english :P

---

### Post by lioninthesky on 2007-09-13
> **robertor said:**
> Well i hace solved my problems. I did a dowgrade of my bios. I was using 1.3309 and i install a 1.3302 and now i don´t have any more problems with the battery.
Greets!
Roberto

This worked for me too.  Now if I could only stop getting the 'soft lockup' messages when coming out of suspend mode.

---

### Post by lioninthesky on 2007-09-13
> **yakolev said:**
> The issue with the black screen logout is common to the video card and a solution is to go to the login options and tick the box for "restart the x server with each login"

I'm considering a bios downgrade but not sure how to go about it, seeing as how it is intended to be done from windows and I'm not particularly enamored with reinstalling vista solely for a bios operation...

Unfortunately, this did not resolve the problem for me.  Although, I should have elaborated more on the problem.  I cant get a terminal session either.  It's as though the back light is killed and sent into suspend mode or something, whenever I log out.

---

### Post by robertor on 2007-09-13
> **lioninthesky said:**
> This worked for me too.  Now if I could only stop getting the 'soft lockup' messages when coming out of suspend mode.

have you ever tried the version of ndiswrapper from the original source? I remove the version from the ubuntu´s packages and i compiled the ndiswrapper 1,47 and all my problems go out (soft bug cpu, freeze detecting and activating the wireless, lose the screen after suspend and wake up).
Really, try and told us how was go on.
Greets!
Roberto

---

### Post by lioninthesky on 2007-09-14
> **robertor said:**
> have you ever tried the version of ndiswrapper from the original source? I remove the version from the ubuntu´s packages and i compiled the ndiswrapper 1,47 and all my problems go out (soft bug cpu, freeze detecting and activating the wireless, lose the screen after suspend and wake up).
Really, try and told us how was go on.
Greets!
Roberto


Thank you sir! That did it and I am very grateful :-)

I'm surprised, I guess a lot of issues where related to the killswitch issue or something.  I no longer have any issues related to the killswitch, after the ndis update.

---

### Post by lioninthesky on 2007-09-14
> **yakolev said:**
> The issue with the black screen logout is common to the video card and a solution is to go to the login options and tick the box for "restart the x server with each login"

I'm considering a bios downgrade but not sure how to go about it, seeing as how it is intended to be done from windows and I'm not particularly enamored with reinstalling vista solely for a bios operation...

Check out [http://www.bootdisk.com](http://www.bootdisk.com).  Make a DOS boot disk, and copy the DOS flash utility and BIOS (from the 3303 folder inside the 3303.zip file) to your boot disk.  Bring your machine up in DOS mode (via boot disk) and then run the flash utility from the 3303 folder.

The BIOS upgrade resolved my issue and all issues that where not related to ndis or sound.  This BIOS version (previously posted) works like a charm:

[ftp://ftp.work.acer-euro.com/notebook/aspire_5050/bios/3303.zip]("ftp://ftp.work.acer-euro.com/notebook/aspire_5050/bios/3303.zip")

I would suggest using the BIOS upgrade above and compiling the latest ndis wrapper.  You'll notice quite a difference.

---

### Post by nosrednaekim on 2007-09-14
Hmm thats one thing that I didn't mention that I did.... compile the latest ndiswrapper driver. Maybe i'd better update my tutorial.

---

### Post by yakolev on 2007-09-18
> **lioninthesky said:**
> Check out [http://www.bootdisk.com](http://www.bootdisk.com).  Make a DOS boot disk, and copy the DOS flash utility and BIOS (from the 3303 folder inside the 3303.zip file) to your boot disk.  Bring your machine up in DOS mode (via boot disk) and then run the flash utility from the 3303 folder.

The BIOS upgrade resolved my issue and all issues that where not related to ndis or sound.  This BIOS version (previously posted) works like a charm:

[ftp://ftp.work.acer-euro.com/notebook/aspire_5050/bios/3303.zip]("ftp://ftp.work.acer-euro.com/notebook/aspire_5050/bios/3303.zip")

I would suggest using the BIOS upgrade above and compiling the latest ndis wrapper.  You'll notice quite a difference.

Thanks! I'll give this a shot once I get a smidge more time...

Now for hoping that the card-reader gets fixed with gutsy's next kernel...

---

### Post by soundwave on 2007-09-25
:? uhhh??? i have BIOS version 1.3309

Did could i downgrade BIOS to version 1.3303 ???

Sorry for my english :S

---

### Post by robertor on 2007-09-25
> **soundwave said:**
> :? uhhh??? i have BIOS version 1.3309

Did could i downgrade BIOS to version 1.3303 ???

Sorry for my english :S

Yes soundwave! You can. I did it and work witrhout problems. I have tried 2 version 1.3302 and 1.3303, and this lastone give me better results.
Greets!
Roberto

---

