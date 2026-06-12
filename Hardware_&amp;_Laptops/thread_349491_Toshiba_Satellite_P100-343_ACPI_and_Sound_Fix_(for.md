---
title: "Toshiba Satellite P100-343 ACPI and Sound Fix (for Bios 3.30)"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by klaas on 2007-01-30
Hi,

Just FYI, i have fixed my sound and ACPI problem (sound only works when ACPI=OFF is added to the kernel boot options) for my Toshiba Satellite P100-343 with UBUNTU Edgy & Feisty. 

Instructions are for EDGY & FEISTY ONLY!!!

*Upgrade your BIOS to version 3.30.
*Download the custom DSDT file for the P100-343 (3.30) from [http://acpi.sourceforge.net/](http://acpi.sourceforge.net/) (via the view menu).
*Backup your "/boot/initrd.img-xxx" and "/boot/vmlinuz-xxx" files (Only for safety).
*Do a "sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml" (Is case sensitive!).
*Do a "sudo dpkg-reconfigure linux-image-$(uname -r)".
*Reboot.

EDIT 1: 
If you experience low sound volume follow the guide at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to install the latest alsa drivers.

EDIT 2:
It also works for FEISTY!

Hoping to help someone with the same problem :) 

Greetz,
Klaas

---

### Post by unamed on 2007-02-02
Hi,I am a noob and have problem with sound and video.with acpi=off on ubunto 6.10 a have sound but don't  have video.I see this post for ACPI and sound fix but i don't how to make patch for kernel.PLS HELP:confused:   



Model Name                    Satellite Pro P100

Part Number                   PSPA4E-00C007EN

BIOS Version                  V3.30

CPU                           Genuine Intel(R) CPU           T1300  @ 1.66GHz

Memory                        1024MB RAM

Video                         NVIDIA GeForce Go 7600   

Screen Resolution             1440 x 900 Pixel

Color Quality                 True Color (32 Bit)

Sound                         Conexant High Definition Audio  in linux=intel hda snd

Network                       Intel(R) PRO/1000 PL Network Connection    

                              Intel(R) PRO/Wireless 3945ABG Network Connection   

Modem                         HDAUDIO Soft Data Fax Modem with SmartCP  

IDE Device 1                  TOSHIBA MK6034GSX

IDE Device 2                  None

IDE Device 3                  HL-DT-ST DVDRAM GMA-4082N   Firmware=HV02

IDE Device 4                  None

IDE Device 5                  DS5859D ZWB734H         1.0 

IDE Device 6                  None

with  acpi=off and latest alsa 1.14rc2 sound working fine but no LAN card staled. How to make the fix pls help me .................................

---

### Post by paddyS on 2007-02-15
So what do those of us with Dapper do ?

---

### Post by arg_ on 2007-02-18
Pardon my ignorance but the DSDT file I download for Toshiba P100-343 is *Toshiba-Satellite_P100-343-3.30-custom.asl.gz* which contains only one file T*oshiba-Satellite_P100-343-3.30-custom.asl*
The command above, *sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml*, is supposed to copy a file named DSDT.aml.  
What am I missing ?

thanks

---

### Post by klaas on 2007-02-19
-@arg_: Sorry my fault, I updated the file on [http://acpi.sourceforge.net/](http://acpi.sourceforge.net/). If you redownload that file you should find the dsdt.aml file inside.

-@paddyS: If you use Breezy or Dapper you should replace the 
"sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml" command with 
"sudo cp dsdt.aml /etc/mkinitramfs/DSDT.aml"

---

### Post by arg_ on 2007-02-19
thank you Klaas for the update.
Unfortunatelly it did not work for me, the system hangs on startup. I tried to boot in recovery mode and while it shows that the customized DSDT is properly loaded, the system hangs later on in *Setting up standard PCI resources*.  Fortunatelly I have a backup to restore - as you wisely suggested :-D 
Maybe my laptop is not exactly configured as yours. The model is P100-138 and bios version is 3.30
This sound problem is frustrating, it is two months now I haven't managed to make it work :(

---

### Post by evanweaver on 2007-02-24
I have a P100-MA6 and was afraid to use Klaas' file since the hardware is a little different, especially considering arg_'s experience.

Instead I implemented Klaas' idea a little differently: I edited the grub menu file (e.g. sudo vi /boot/grub/menu.lst) - use your favourite editor if you don't know how to work vi! - and added
[INDENT]acpi=off[/INDENT]
to the end of the line for the kernel I boot (my change in [COLOR="Blue"]blue[/COLOR]):
[INDENT]
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro quiet splash [COLOR="Blue"]acpi=off[/COLOR]
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot[/INDENT]

Now the sound works fine, but the fan blows all the time instead of only when things get warm (so it is noisier).

---

### Post by arg_ on 2007-03-11
Sound at last!
I tried another DSDT custom file, Toshiba-Satellite_P100-JR100E-3.30-custom.asl, and finally I have _both_ ACPI and sound in my P100-138 (conexant  CX20551 chip).

Thanks Klaas and everyone for helping us linux newbies ;)

---

### Post by chamiltonj on 2007-03-11
For the record, the instructions in the OP work perfectly for the Toshiba Sattellite P105-S6227.  
Thanks for this! :)

---

### Post by EndPerform on 2007-03-12
> **chamiltonj said:**
> For the record, the instructions in the OP work perfectly for the Toshiba Sattellite P105-S6227.  
Thanks for this! :)

That's the exact model of my laptop, too.  Good to know it's working in Edgy, at least.  I've been running Feisty and could not get the fix to work like this.  Looks like I'm going to have to go ahead and install Edgy and try it.  I miss my sound.

---

### Post by klaas on 2007-03-12
Glad that I could help some people :-)

It seems that this method will not work with Feisty because custom dsdt is not supported in the current feisty kernel: [http://ubuntuforums.org/showthread.php?p=2123354#post2123354](http://ubuntuforums.org/showthread.php?p=2123354#post2123354)

I hope this will be fixed in the final release!

Klaas

---

### Post by EndPerform on 2007-03-12
Yeah, I do hope they take care of it.  I tried one of the other methods mentioned from the Gentoo wiki (the method where you go into the kernel config and specify a path to a custom DSDT), but again in Feisty, that's a no go.  I'm hoping they decide to include something along those lines.

---

### Post by EndPerform on 2007-03-13
Got it working based on the instructions.  I'm running Edgy now.  I'm thinking about attempting an upgrade to Feisty to see if I can run it with the Edgy kernel.  I need to check Launchpad and see if there's any word on whether or not the devs are going to include custom DSDT support in the kernel, or if they're gonna fix up the kernel.

---

### Post by klaas on 2007-03-13
The Ubuntu team has confirmed the problem and will try to fix it for the next feisty release (see last comment in launchpad for bug 83544).

---

### Post by EndPerform on 2007-03-15
Thanks klaas.  I've been keeping an eye on that bug, and according to launchpad they have a fix.  I'm guessing the next test release should have it in, which is definitely good news.  Thanks again for your work with the DSDT stuff, I appreciate it.

---

### Post by kombinator on 2007-03-23
Just so anyone googling like I did finds out...I have a PSPA3C-SD300E, and the JR100E DSDT works perfectly.  I researched a bit before I installed it, and I noticed the PSPA3C prefix applies to the Canadian release widescreen Toshiba desktop replacements, which I venture a guess run the same Conexant chipset.

Anywho, don't quote me on that if you have a different brand PSPA3C from Canada and the JR100 DSDT blows it up or something. :) 


I guess windows is going in the garbage pretty soon...and here I went through all that trouble setting up a dual-boot and backing up everything in case the sound didn't work...

Sheesh. ](*,)

Anyway, good to be a brand nubcake in the Ubuntu world.  I love you guys.  Really.

---

### Post by EndPerform on 2007-03-27
Well, tonight I'm going to find out if the newest Feisty kernel has this fix in it or not.  Going to do a fresh install of the latest beta and see what happens.  I'll post back with my results.

**Update:**
Working like a charm now.  Good stuff!

---

### Post by rax_m on 2007-04-16
I tried this fix for the Toshiba P100-429 (PSP3AE) and unfortunately it doesn't seem to work. 
I downloaded the custom DSDT for the P100-429 and upgraded the bios to 3.3 as recommended but no luck. 

Sound is from the Conexant CXT5047 chip set. 

If anyone knows of a solution please help :) 

Thanks 
Rax

---

### Post by Tyriel on 2007-04-20
By using this guide and recommended file I just got sound working on my Toshiba Satellite P105 S9312 with BIOS version 3.30 with Feisty.  Thank you for the help Klaas keep up the great work.  :)

---

### Post by nystire on 2007-04-24
Has anybody tried this on a Toshiba P105-9337? It isn't my Laptop, so I'm a bit hesitant to play around with it, but it's owner REALLY wants to ditch Vista...

---

### Post by Tyriel on 2007-05-01
Hi klaas, I was wondering if you or anyone else could possibly please explain how I could install an asl file instead of an aml.  I have had no luck in this so far.  The only reason I ask is that I found one for my exact model of laptop that fixes an nvidia issue with its fan not spinning.

---

### Post by Tom Tiger on 2007-05-01
Good Work Klaas :-)  Many thanks from a Toshiba TASC Centre :)

---

### Post by JEP on 2007-05-03
I have a Toshiba P100-MA2 PSPA3C.  It looks quite similar to the J100E, for which there is a custom, apparently working DSDT.

My question is, if I follow the instructions here, will I screw up other items such as video?  The card is a GeForce 7600, whereas the J100E has a 7300.  Mine is also a Core 2 Duo, instead of Core Duo. Are there any instructions anywhere on creating or customizing a DSDT?  It must be newbie-friendly...

I have entered the bug in launchpad, [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110395](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110395) but after a week the importance is still undecided.  From this and the fact that the Ubuntu Audio Team have 97 bugs assigned, some of them 6 months old, I assume I should not hold my breath for a fix.

---

### Post by HugoPalma on 2007-05-03
> **JEP said:**
> I have a Toshiba P100-MA2 PSPA3C.  It looks quite similar to the J100E, for which there is a custom, apparently working DSDT.

My question is, if I follow the instructions here, will I screw up other items such as video?  The card is a GeForce 7600, whereas the J100E has a 7300.  Mine is also a Core 2 Duo, instead of Core Duo. Are there any instructions anywhere on creating or customizing a DSDT?  It must be newbie-friendly...

I have entered the bug in launchpad, [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110395](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110395) but after a week the importance is still undecided.  From this and the fact that the Ubuntu Audio Team have 97 bugs assigned, some of them 6 months old, I assume I should not hold my breath for a fix.

I have a Toshiba P100-103 and these([http://www.linuxquestions.org/questions/showthread.php?t=531575](http://www.linuxquestions.org/questions/showthread.php?t=531575)) worked great for me.

---

### Post by JEP on 2007-05-07
I have read that post and was sufficiently scared off by the first warning, about it being invalid if I was running BIOS 3.3.0, which I am, that I didn't try it.

My question was, what happens if parts of the DSDT file do not match my hardware?

---

### Post by krantix on 2007-05-09
does anybody know how to fix audio and acpi with bios 3.5? I've tryed many dsdt but none works! i can get audio on but then my GPU fan is almost everytime off and my nvidia gets to 120°!!! please help!

---

### Post by JEP on 2007-05-15
So I guess that's it?  Looks like I bought the wrong laptop.  Funny, but the last two desktops I bought were also unable to use ACPI, seems to be pretty crappy technology.

Back to Windows I go!

---

### Post by HugoPalma on 2007-05-15
I followed that post and it worked great for my 3.30 version BIOS.

You should give it a try...

---

### Post by JEP on 2007-05-15
As I have a different model than you do, my question remains, what happens when you load a DSDT file for incorrect hardware?  For example, I have a different CPU and sound card than you do.  My assumption is that my hardware will not work correctly if I load the wrong DSDT.

I would create an accurate DSDT, but have no idea how to do so.

---

### Post by HugoPalma on 2007-05-16
> **JEP said:**
> As I have a different model than you do, my question remains, what happens when you load a DSDT file for incorrect hardware?  For example, I have a different CPU and sound card than you do.  My assumption is that my hardware will not work correctly if I load the wrong DSDT.

I would create an accurate DSDT, but have no idea how to do so.

You won't be loading the same DSDT that i do. The tutorial doesn't give you a DSDT to use, it tells you how you can modify the one you already have to make it work properly. Anyway, the tutorial also tells you how you can make a backup your current DSDT, so if anything goes wrong all you have to do is use the old one again. I didn't get it right the first time and i had no problem going back to the old configuration.

---

### Post by JEP on 2007-05-16
What tutorial are you referring to?  The one about a P100 on SLED 10 at [http://www.linuxquestions.org/questions/showthread.php?t=531575](http://www.linuxquestions.org/questions/showthread.php?t=531575)

It is not at all clear that this will work on Ubuntu Feisty, which is what I have, and it also has an update saying that it is not necessary to use the custom DSDT at all, but simply to update alsa to 1.0.14rc3...

I guess I will try it and see what happens.

---

### Post by HugoPalma on 2007-05-16
> **JEP said:**
> What tutorial are you referring to?  The one about a P100 on SLED 10 at [http://www.linuxquestions.org/questions/showthread.php?t=531575](http://www.linuxquestions.org/questions/showthread.php?t=531575)

It is not at all clear that this will work on Ubuntu Feisty, which is what I have, and it also has an update saying that it is not necessary to use the custom DSDT at all, but simply to update alsa to 1.0.14rc3...

I guess I will try it and see what happens.

Yes, i am refering to that tutorial. I'm running Feisty also and it worked for me.
I didn't try the alsa upgrade. Please post to this thread if just updating alsa worked.

---

### Post by JEP on 2007-05-16
Wow, what a load of partial misinformation.  I have yet to encounter a procedure for Linux that works as written.  After many workarounds for things that simply did not work,  installing ncurses, gettext, and several other items not mentioned, the alsa-update produced - a silent laptop!

I then decided to follow your advice and try the method described in the page [http://www.linuxquestions.org/questions/showthread.php?t=531575](http://www.linuxquestions.org/questions/showthread.php?t=531575), although its written for SLED and not Ubuntu.  I got as far as "vi /etc/sysconfig/kernel", and hey, there is no such directory on my system.  Any hints?

Edit: Never mind, I found this info:

*Backup your "/boot/initrd.img-xxx" and "/boot/vmlinuz-xxx" files (Only for safety).
*Do a "sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml" (EDGY specific).
*Do a "sudo dpkg-reconfigure linux-image-$(uname -r)".
*Reboot.

Worked great! I finally have sound!  I doubt if I could tell you the steps I took, too many to count now.

---

### Post by hondaman on 2007-05-16
This worked for my new Toshiba p105-s9337

Many many thanks!

---

### Post by Ryanson on 2007-05-20
I am stuck on this part:

*Do a "sudo dpkg-reconfigure linux-image-$(uname -r)".

I am not sure what exactly to put there. Sorry if this sounds stupid, but I've not worked much with this.

---

### Post by yco on 2007-05-20
> **rax_m said:**
> I tried this fix for the Toshiba P100-429 (PSP3AE) and unfortunately it doesn't seem to work. 
I downloaded the custom DSDT for the P100-429 and upgraded the bios to 3.3 as recommended but no luck. 

Sound is from the Conexant CXT5047 chip set. 

If anyone knows of a solution please help :) 

Thanks 
Rax

I managed to make sound working on this machine with ACPI=OFF just argument adding IRQPOLL

kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=960bddad-57bc-4486-90c5-75f56417cd54 ro quiet splash **acpi=off irqpoll**

---

### Post by cptcrunch on 2007-05-21
> **kombinator said:**
> Just so anyone googling like I did finds out...I have a PSPA3C-SD300E, and the JR100E DSDT works perfectly.  I researched a bit before I installed it, and I noticed the PSPA3C prefix applies to the Canadian release widescreen Toshiba desktop replacements, which I venture a guess run the same Conexant chipset.

Anywho, don't quote me on that if you have a different brand PSPA3C from Canada and the JR100 DSDT blows it up or something. :) 


I guess windows is going in the garbage pretty soon...and here I went through all that trouble setting up a dual-boot and backing up everything in case the sound didn't work...

Sheesh. ](*,)

Anyway, good to be a brand nubcake in the Ubuntu world.  I love you guys.  Really.

how did you get sound, i have the exact same system, but i don't know how to upgrade my firmware??? My BIOS is via pheonix

---

### Post by cptcrunch on 2007-05-21
> **cptcrunch said:**
> how did you get sound, i have the exact same system, but i don't know how to upgrade my firmware??? My BIOS is via pheonix

PSPA3C-SD300E does not have a bios upgrade so what now???My bios is V1.50

---

### Post by cptcrunch on 2007-05-21
still no luck with sound :(

---

### Post by cptcrunch on 2007-05-21
kombinator:

please post the steps... we'd like to know

---

### Post by cptcrunch on 2007-05-22
bump

---

### Post by JEP on 2007-05-24
> **Ryanson said:**
> I am stuck on this part:

*Do a "sudo dpkg-reconfigure linux-image-$(uname -r)".

I am not sure what exactly to put there. Sorry if this sounds stupid, but I've not worked much with this.

Just type it in exactly as you see it.  "$(uname -r)" is a system call to substitute the actual kernel version.

---

### Post by JEP on 2007-05-24
> **cptcrunch said:**
> PSPA3C-SD300E does not have a bios upgrade so what now???My bios is V1.50

I found that exact model number on Toshiba's website with a BIOS update to 3.30

---

### Post by cptcrunch on 2007-05-24
> **JEP said:**
> I found that exact model number on Toshiba's website with a BIOS update to 3.30

Thanks, I just found it as well

---

### Post by cptcrunch on 2007-05-24
Sound At Last with ACPI on!!!!!!!! Thanks!!!!

No need to stick with XP now. BYE BYE windows :)

---

### Post by bernhar on 2007-05-31
Just got the file for my toshiba p105-s6177:

Toshiba-P105-S6177-3.30-custom.asl.gz

On the other hand, there is no DSDT.aml file! I just have one file inside the pack:

Toshiba-P105-S6177-3.30-custom.asl

So, I just got thisngs messed up. I've got a kernel panic here, hehehe...

No problem. I'll just install it over again, but cn you please help me figure this out?

THANX!

---

### Post by cptcrunch on 2007-06-01
if you click the Toshiba-P105-S6177-3.30-custom.asl file, another window should pop up and you should be able to see and copy the dsdt.aml file.


Cheers

---

### Post by robo-linux on 2007-07-03
Hi Klaas,

I have a Tohiba laptop P105-S9337
and I have tried following your instructions to 
get sound working, but it does not work for me.
I am now trying to download different custom DSDT files but
sourcefourge downloads do not come down anymore.

Any suggestions? I have spent a week working on this so
far. 

Thank you very much.

---

### Post by sw_ on 2007-07-04
my laptop is a Toshiba Satellite P100-354 and my BIOS ver. is 3.80.
i tried just about any tutorial and how-to to get my sound working - didn't manage to compile the newest alsa for some reason though...

then i stumbled over this thread and searched on the acpi site for my notebook model, but it isn't listed - does anyone know an equivalent model listed in the DSDT page? or any other possibility to get my sound working?

---

### Post by jessi3k3 on 2007-07-13
> **robo-linux said:**
> Hi Klaas,

I have a Tohiba laptop P105-S9337
and I have tried following your instructions to 
get sound working, but it does not work for me.
I am now trying to download different custom DSDT files but
sourcefourge downloads do not come down anymore.

Any suggestions? I have spent a week working on this so
far. 

Thank you very much.
Yo. I have the same exact laptop and I fixed the issue. I had to edit the DSDT on my own because every laptop had the 3.30 BIOS while I had the 3.80 BIOS. It really takes one day of dedication to pull off. I was lost for the past week but now everything works fine.
> **sw_ said:**
> my laptop is a Toshiba Satellite P100-354 and my BIOS ver. is 3.80.
i tried just about any tutorial and how-to to get my sound working - didn't manage to compile the newest alsa for some reason though...

then i stumbled over this thread and searched on the acpi site for my notebook model, but it isn't listed - does anyone know an equivalent model listed in the DSDT page? or any other possibility to get my sound working?

Just like I told the person above your stuck with modifying your own DSDT. That's what I did because I have the 3.80 BIOS. I have everything working now.

I would be glad to post my dsdt file but I dont know where to upload it to.

---

### Post by ASD2003ru on 2007-07-13
I have P100-387 + Festy and install as post #1 but not work.
If in menu.lst write ACPI=off then sound work but Nvidia driver not work :(

---

### Post by kurdy_de on 2007-07-16
I uploaded a fixed DSDT file to [http://acpi.sourceforge.net](http://acpi.sourceforge.net) for Toshiba Satego P100-490 (PSPAME) Bios 3.80. Basically there were the same changes to do in the DSDT.dsl file as for the 3.30 Bios.

Sound works great now and with new NVIDIA proprietary driver also my GPU fan works correctly.

For other supported Toshiba models refer to the german support (or maybe other european Toshiba support sites) and find the SATEGO P100-490. Look for the 3.80 Bios update. When opening the detailed view other supported models are listed.

---

### Post by sw_ on 2007-07-25
dude, thanks for the fixed DSDT - it also worked for my P100-354 (PSPA6E)
now i can finally use linux on my laptop as my main OS again:)

---

### Post by EndPerform on 2007-08-01
Unfortunately I lost the DSDT.aml file when I had to blow my laptop away.  I tried to download it again using the DSDT I had before, but the archive doesn't have the .aml file in it.  Anyone have a DSDT.aml file for P105-6227 or even from the original post on this thread?

---

### Post by doctorbaldwin on 2007-08-05
Wow.  Klaas.  Thanks for figuring this out!  I've been trying to get a good copy of Linux fully functional on my laptop for about a year now (off and on, I ended up resorting to Windows).  Here's what worked for me:

Satellite P100-ST7211
BIOS 3.80
Kernel 2.6.20-16
ALSA 1.0.14rc4

Not sure if you need to upgrade your ALSA drivers beyond what is standard like I did, but I wanted everything as recent as possible.  Klaas's instructions may not work for older kernels though (like 2.6.9 and earlier).

DSDT file:  Toshiba P100-ST9762 obtained from [http://acpi.sourceforge.net/dsdt/view.php]("http://acpi.sourceforge.net/dsdt/view.php")

I followed klaas's instructions with only a couple tweaks.  
I downloaded the file
Did "gunzip  ~/Desktop/Toshiba-P100-ST9762-3.50-original.asl.gz"
Did "sudo cp ~/Desktop/Toshiba-P100-ST9762-3.50-original.asl /etc/initramfs-tools/DSDT.aml"

Just a matter of changing file names for me and using a dsdt for a machine closer to mine.  Hot dang, we're live folks!

---

### Post by EndPerform on 2007-08-07
Yeah, I renamed the file that I used previously.  It got loaded, but no sound for me now.  It's really odd since it used to work.  Guess I'll have to do a bit more digging on this one.

---

### Post by eMcJagger on 2007-08-07
HELP!  I tried to follow this method (adapted), and now not only do I have no sound, I have no graphics!

I have a toshiba satellite p100 PSPAEC-JL407C, with NVIDIA GeForce Go 7300.  I recently upgraded the bios to 3.80 (using windows - I have a dual-boot).

I tried to follow doctorbaldwin's example, first with Toshiba-Satellite_P100-343-3.30-custom.asl and then Toshiba-Satellite_P100-PSPA3E-3.30-custom.asl (which I thought a closer match to my model), and then copying them to /etc/initramfs-tools/DSDT.aml.  I'm not sure the exact order of operations, but after several attempts and reboots, the sound never came, and eventually I lost the graphics as well.  The boot process just gets to "Running local boot scripts (/etc/rc.local)" and then I get a login prompts.

I've included the following files, which I thought might be of use:

/boot/grub/menu.lst

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet video=vga16fb:off video=vesafb:off

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,7)
#kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off acpi=off
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.20-15-386
savedefault

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.17-11-386
savedefault

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.17-10-386
savedefault

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.17-10-386

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, kernel 2.6.15-28-686
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-28-686 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.15-28-686
savedefault

title		Ubuntu, kernel 2.6.15-28-686 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-28-686 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.15-28-686

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.15-28-386
savedefault

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-27-686 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.15-27-686
savedefault

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-27-686 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.15-27-686

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.15-27-386
savedefault

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.15-27-386

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault

title		Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.15-26-k7

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-686 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.15-26-686
savedefault

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-686 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.15-26-686

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro quiet video=vga16fb:off video=vesafb:off
initrd		/boot/initrd.img-2.6.15-26-386
savedefault

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=eb80b664-1164-408b-9e79-674d310ad83c ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


```


/etc/X11/xorg.conf

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

l
```


/var/log/Xorg.0.log

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux jeremy-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug  7 11:46:48 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1179,ff31 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1179,ff31 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1179,ff31 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1179,ff31 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1179,ff31 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1179,ff31 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1179,ff31 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1179,ff31 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1179,ff31 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1179,ff31 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d7 card 1179,ff31 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 8086,109a card 1179,ff31 rev 00 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 8086,4222 card 8086,1040 rev 02 class 02,80,00 hdr 00
(II) PCI: 0a:04:0: chip 104c,8039 card 3000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 0a:04:1: chip 104c,803a card 1179,ff31 rev 00 class 0c,00,10 hdr 80
(II) PCI: 0a:04:2: chip 104c,803b card 1179,ff31 rev 00 class 01,80,00 hdr 80
(II) PCI: 0a:04:3: chip 104c,803c card 1179,ff31 rev 00 class 08,05,01 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,11), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x54000000 - 0x540fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x54100000 - 0x541fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:2), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 10: bridge is at (0:30:0), (0,10,14), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 10 I/O range:
	[0] -1	0	0x00003000 - 0x00003fff (0x1000) IX[B]
(II) Bus 10 non-prefetchable memory range:
	[0] -1	0	0xd2100000 - 0xd21fffff (0x100000) MX[B]
(II) Bus 10 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 11: bridge is at (10:4:0), (10,11,14), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 11 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
(II) Bus 11 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation Quadro NVS 110M / GeForce Go 7300 rev 161, Mem @ 0xd1000000/24, 0xc0000000/28, 0xd0000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd2102800 - 0xd21028ff (0x100) MX[B]
	[1] -1	0	0xd2101000 - 0xd2101fff (0x1000) MX[B]
	[2] -1	0	0xd2104000 - 0xd2107fff (0x4000) MX[B]
	[3] -1	0	0xd2102000 - 0xd21027ff (0x800) MX[B]
	[4] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[5] -1	0	0x54000000 - 0x5401ffff (0x20000) MX[B]
	[6] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[7] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[8] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[12] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[13] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd2102800 - 0xd21028ff (0x100) MX[B]
	[1] -1	0	0xd2101000 - 0xd2101fff (0x1000) MX[B]
	[2] -1	0	0xd2104000 - 0xd2107fff (0x4000) MX[B]
	[3] -1	0	0xd2102000 - 0xd21027ff (0x800) MX[B]
	[4] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[5] -1	0	0x54000000 - 0x5401ffff (0x20000) MX[B]
	[6] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[7] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[8] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[12] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[13] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2102800 - 0xd21028ff (0x100) MX[B]
	[5] -1	0	0xd2101000 - 0xd2101fff (0x1000) MX[B]
	[6] -1	0	0xd2104000 - 0xd2107fff (0x4000) MX[B]
	[7] -1	0	0xd2102000 - 0xd21027ff (0x800) MX[B]
	[8] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[9] -1	0	0x54000000 - 0x5401ffff (0x20000) MX[B]
	[10] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[11] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[18] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[19] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2102800 - 0xd21028ff (0x100) MX[B]
	[5] -1	0	0xd2101000 - 0xd2101fff (0x1000) MX[B]
	[6] -1	0	0xd2104000 - 0xd2107fff (0x4000) MX[B]
	[7] -1	0	0xd2102000 - 0xd21027ff (0x800) MX[B]
	[8] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[9] -1	0	0x54000000 - 0x5401ffff (0x20000) MX[B]
	[10] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[11] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[18] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[19] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2102800 - 0xd21028ff (0x100) MX[B]
	[5] -1	0	0xd2101000 - 0xd2101fff (0x1000) MX[B]
	[6] -1	0	0xd2104000 - 0xd2107fff (0x4000) MX[B]
	[7] -1	0	0xd2102000 - 0xd21027ff (0x800) MX[B]
	[8] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[9] -1	0	0x54000000 - 0x5401ffff (0x20000) MX[B]
	[10] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[11] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[21] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[22] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[28] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[29] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

l
```


Let me know if there are any other files or info I should post - I'm obviously a bit out of my depth.  Any help at all appreciated - the original goal of getting sound working would be nice, but right now, I'd be happy to just get my graphics back!

Many thanks!

---

### Post by LuisC-SM on 2007-09-06
It most likely seem to be corrupted. This has nothing to do with your xorg.conf or any other file

Your closest match is for v3.30 not for 3.80

So I suggest you to downgrade to v2.40 there are much more possibilities to fix it than the 3.30 or 3.80 (Thats for geeks :D)

Regards

Luis

---

### Post by candive on 2007-09-27
I almost upgraded my BIO's to 3.8. 
I stopped as soon as I saw Windows Vista Compatible.
And a warning that once upgraded to 3.8 downgrading would not be possible.

I am trying to get away from everything Windows!
Right now I do not like anything about the new Windows or the dishonesty.

I do not want to make any mistakes period, I only want sound for my Feisty Fawn.
If it is that difficult, I will keep my Dual Boot.

---

### Post by LuisC-SM on 2007-09-27
The 3.8 BIOS upgrade was made due to a direct INTEL request to fix v3.30 buggy BIOS.

Right in this moment I have installed v3.80 but I get no sound even with 2.6.22 Gutsy Kernel, but I have read that this kernel has already fixed the fan and the sound problem but there are 3 additional tweaks we must make in some file (maybe make.conf) in order to get it working but I just  can not recall where I saw it :$, and I remember that there is no need to go through all that.

I will update this post when I get it working ASAP.

Regards

Luis

---

### Post by jessi3k3 on 2007-09-30
> **LuisC-SM said:**
> The 3.8 BIOS upgrade was made due to a direct INTEL request to fix v3.30 buggy BIOS.

Right in this moment I have installed v3.80 but I get no sound even with 2.6.22 Gutsy Kernel, but I have read that this kernel has already fixed the fan and the sound problem but there are 3 additional tweaks we must make in some file (maybe make.conf) in order to get it working but I just  can not recall where I saw it :$, and I remember that there is no need to go through all that.

I will update this post when I get it working ASAP.

Regards

Luis
Care to PM me whenever you find out? I also updated to Gutsy today soon to find out my sound wasnt working anymore. I am running BIOS v 4.10 and before Gutsy sound and everything worked fine. All that's not working now is the sound, fans run fine, etc.

One thing I notice now is that the power settings are a bit sluggish in Gutsy. I plug or unplug my laptop and it takes a minute to record the change. Also another thing is that it no longer tells me how much time it takes for my battery to run out.

---

### Post by LuisC-SM on 2007-10-02
> **jessi3k3 said:**
> Care to PM me whenever you find out? I also updated to Gutsy today soon to find out my sound wasnt working anymore. I am running BIOS v 4.10 and before Gutsy sound and everything worked fine. All that's not working now is the sound, fans run fine, etc.
Yup, u can count on that...
> 
One thing I notice now is that the power settings are a bit sluggish in Gutsy. I plug or unplug my laptop and it takes a minute to record the change. Also another thing is that it no longer tells me how much time it takes for my battery to run out.
Well, I forgot to mention that too...
What I can see is that ubuntu's kernell will be ready when the the final gutsy is released, the guys at launchpad (developers) are being very serious with all bugs submitted. I must say that I have a good feeling on that :) 
In the meantime I went back to Feisty with my personal laptop, as I must finish some work this week but I'll be back with gutsy by Thursday or Friday( this week also).
Regards
Luis
Regards

EDIT: I have the DSDT.aml for BIOS v3.8 and v4.0 (with no errors and warnings) ready if anyone wants it. v3.8 was not hacked by me, and the credit goes for Martin LORANG from Gentoo forum. v4.0 was completely hacked by me but I want to make a major hack to keep the temperature as low as 55ºC as suggested by the same guy. Right now I've notice (on feisty) that my temperature is as low as 55ºC so, as said before, just PM me if anyone is interested. 
My laptop model is a Toshiba Satellite P105-sp921 (PSPA6U) but is compatible with a lot of P100 and P105 models

---

### Post by gene6482 on 2007-10-03
Does the sound work with the updated bios?

---

### Post by LuisC-SM on 2007-10-03
> **gene6482 said:**
> Does the sound work with the updated bios?
For gutsy; as said before, there are really kernel issues and there's no chance until a major kernel fix.. Sounds works just perfect in Feisty with any of the DSDT.aml files depending on which BIOS you have installed.
Just remember I said BIOS v2.40, v3.8 and v4.0
Regards
Luis

EDIT:. I will continue using BIOS 3.8 as far as I have found that temperature is not higher than 55ºC and The security hacked made by toshiba does not really affect me as I'm running only linux (windows only runs under VM)

---

### Post by jessi3k3 on 2007-10-04
So Luis, Do you think we can expect a new updated Kernel by the time Gutsy is fully released? Is there a way I can "downgrade" to Feisty? I think I should be asking this in another help forum.

---

### Post by LuisC-SM on 2007-10-04
> **jessi3k3 said:**
> So Luis, Do you think we can expect a new updated Kernel by the time Gutsy is fully released? Is there a way I can "downgrade" to Feisty? I think I should be asking this in another help forum.
Hi Jessi.
I really think this sound issue will be fixed when Gutsy Gibbon goes to final. But I do not think they will bring us the completely patched one (as I read someplace) that has some other usb enhancements, but I might be completely wrong (which I hope) and we could have the last patched one (vanilla).
I do not really know how to down grade to Feisty, What I now do is a completely Home and System back up and I just reinstall everything to its last stage.
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
Hope to have been helpfull enough
Kind Regards
Luis

---

### Post by gene6482 on 2007-10-04
if i've upgraded from feisty to gutsy, will i be able to use an older kernel version

---

### Post by LuisC-SM on 2007-10-04
> **gene6482 said:**
> if i've upgraded from feisty to gutsy, will i be able to use an older kernel versionI doubt it. But I cannot say no as far as I'm not an expert.
From a ubuntu custom kernel to a vanilla is always possible but I've never seen this backwards.
Cheers
Luis

---

### Post by gene6482 on 2007-10-05
i saw there was a kernel update, but haven't had a chance to update yet, did that help at all?

---

### Post by LuisC-SM on 2007-10-05
> **gene6482 said:**
> i saw there was a kernel update, but haven't had a chance to update yet, did that help at all?

@#&%(/)........... lol (just a joke)

TTYTT (To tell u the truth).... Tomorrow I will see what's going on... please.. hang on, dont desperate, I'm 99.99% there will be JUST GOOD NEWS :D, 
I really wish to give u just good news, but  I DO have a lot of work.... just let me sleep tonight and I''ll wake up with a straight answer (I've not been able to sleep for 22 hours)
key, what about trying with that kernel update?.. I can deliver just the 3 DSDT.aml files so you start trying... you will not break your system, (believe in me :) )
Let me know SVP... and I'll do it ASAP
Regards
Luis

PS. show me the way to upload the files SVP in a thread so anyone who feels with enough *NIX strength can just give it a try. (as said before, I'll guide u so u do not break your system) :D  (Uhmmm, may beeee)

---

### Post by gene6482 on 2007-10-06
i can do the dsdt, but when i posted i hadn't had a chance to look at the new kernel yet.  I plan on doing some testing today.  Would you recommend upgrading my bios?  I currently have 3.3

---

### Post by LuisC-SM on 2007-10-06
> **gene6482 said:**
> i can do the dsdt, but when i posted i hadn't had a chance to look at the new kernel yet.  I plan on doing some testing today.  Would you recommend upgrading my bios?  I currently have 3.3

Well, I had really BIG problems with that BIOS, but then, I was not involved in the IASL language, and I was completely noob to try to hack it. In gentoo forums a lot of people had trouble and went back to 2.40. Later, I discovered that someone had already hacked it and made a good DSDL.aml but I never tried it.
Someplace I've read that Intel directly asked Toshiba to fix that  BIOS as far as they also found lots of bugs so Toshiba came up with v3.80. Toshiba themselves had post to upgrade to 3.8 and later to 4.0. But I read that this upgrade (4.0) was meant for vista users.
So, the choice is yours. if you have a BIOS v3.30 and you are using a hacked DSDT.aml and you feel comfortable enough and all works just well... I don't really see a reason, except for the fact that you want everything up-to-date.
Cheers
Luis

PS. I'm not really involved in any programming language except that I now understand how IASL works. So do not expect me to be a geek :D I've used this laptop as a learning lab in my spare time,

---

### Post by gene6482 on 2007-10-06
I'm pretty much the same way.  Got my laptop with vista on it, hated it so decided to make the switch.(was dual-booting my Desktop at the time with Fedora).  Now both machines run Ubuntu.  I guess I'll try it, since fixing the dsdt was pretty easy the first time.  As for Intel recommending it, it actually says that in the release notes for the bios update on toshiba's site. :)

---

### Post by LuisC-SM on 2007-10-06
Hi

The good news... 
1) Kernel upgrade to 2.6.22-13
2) With that kernel upgrde my fingers are not burning anymore, so that means the fans are working just perfect (even without the DSDT.aml)
my acpi -V shows me this:
> Battery 1: charged, 100%
     Thermal 1: ok, 44.0 degrees C
  AC Adapter 1: on-line

The bad news....
1) Still no SOUND (it has nothing to do with ALSA)
2) The window bar keeps disappearing 

Sorry to bring bad news.. I've been here for more than 9 hours and I'm very tired of trying everything I know, I must go to eat something and play ewith my children a little bit :) so in the midnight I'll probabily bring some news

Cheers

Luis

---

### Post by LuisC-SM on 2007-10-06
Could someone try this:
```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
```
and see if it works? (sound)

---

### Post by jessi3k3 on 2007-10-07
Luis, same problem. Compiz keeps on crashing it's not even funny. I cant move any windows, my resolution is messed up. I cant boot with the new Kernel because it doesnt recognize my video card. Basically I wiped Gutsy off of my laptop and sticking to Feisty till a stable version of Gutsy comes out.

---

### Post by LuisC-SM on 2007-10-07
LOL...

Well, before I saw your post I was really laughing, my laptop's bright went down... I cannot boot in 2.6.22-13-generic anymore, 

The bad is that I cannot make the monitor's bright go higher, the good is my geek neighbor is coming tonight to see if he can fix the brightness issue.

For the sound... he said to me.......... WAIT FOR THE FINAL RELEASE!!!!!

So... I'll wait :lolflag:

PS. He has the same sound issue as all of usand he does not want to fix it  :confused:

---

### Post by geopgeop on 2007-10-10
[FONT=Tahoma]I have a Toshiba Satellite P105-S6114, and used Feisty on it for quite a while.  I tried upgrading from Feisty to Gutsy and sound stopped working.  I then tried a clean install of Gutsy, applied the DSDT.aml to /etc/initramfs-tools/, and sound still didn't work.  I then added the Feisty repos in (not the best idea) and installed its latest kernel image, restricted modules, and headers (version 2.6.20-16), booted from the old kernel, and sound works, confirming that Gutsy introduced a regression.

The laptop has Intel 82801G/ICH7 with Conexant CX20551 codec, so snd-hda-intel is used.  The ALSA drivers themselves shouldn't be the problem, since they work with the older kernel.

I'd like to know what changed from Feisty's kernel to Gutsy's kernel that caused this to happen so I can have a kernel from Gutsy with sound.  If such a fix can't be added to Gutsy right now, simply because it's about to be officially released, at least give us P105 owners a step-by-step guide to implement that fix ourselves.  It was hard enough hacking the DSDT just to get sound working in Feisty (the reason this thread was made in the first place), don't let us suffer more.  At least I'm happy not having to use the 915resolution package anymor[/FONT][FONT=Tahoma]e for my 1440x900 screen.

Laptop specifications:
Toshiba Satellite P105-S6114, BIOS version 3.80
Intel 82801G/ICH7 Family with Conexant CX20551 codec
First partition: Windows Vista
Second partition: Ubuntu
Third partition: Toshiba Express Media Player (InterVideo/Corel InstantON, based on Linux)

My steps:

1.  Install Gutsy beta from CD.
2.  Apply DSDT fixes.
3.  Add Feisty repositories.
4.  Install linux-image-2.6.20-16, linux-headers-2.6.20-16, and linux-restricted-modules-2.6.20-16.
5.  Restart; in GRUB, boot from 2.6.20-16
6.  (Optional) remove Feisty repositories (to reduce other conflicts) and leave the 2.6.20-16 packages installed as local.

Sound works that way, but it's using the kernel from Feisty, which is undesired.
[/FONT][FONT=Tahoma][FONT=Courier New][FONT=Tahoma][FONT=Courier New][FONT=Tahoma][/FONT][/FONT][/FONT][/FONT][/FONT]

---

### Post by LuisC-SM on 2007-10-10
This has been discussed here:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134146](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134146)
and here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469) (duplicate)
I'd like to have sound back with kernel 2.6.22-9 as far as this kernel has a lot of enhancements for usb webcams and photo cams and a lot more.
I'd really like to breake my system (once again lol) but don't want to stop trying to get a temporary fix.
And by the way.... thanks for the info.
Luis

---

### Post by Tyriel on 2007-10-10
Hey guys, I too am having this same problem with sound. I'll do some research and hope that I can help find solution.

---

### Post by LuisC-SM on 2007-10-10
Hi.
After the new kernel update (2.6.22-14-generic), I still have no sound.
As suggested in launchpad, I have already patched lum with this new kernel and no sound.
What I will now now is to try to install kernel 2.6.22-10 and wil apply all those fixes one by one and will see which one works, however, this is a development version so we can still play around a little bit before "final" is available.
I hope not to come back with a unusable laptop  :lolflag:
cheers
Luis

PS, oh, and Tyrel,... welcome to the club :D

---

### Post by Tyriel on 2007-10-10
Sorry if I missed this already in this thread but if you boot with acpi=off like the original issue of this thread you have sound.  Unfortunately that is just not a great idea for us laptop users.

Haha thanks Luis although this was one club I wish I was not apart of :-P

---

### Post by LuisC-SM on 2007-10-11
Nah....
Before I boot ACPI=off I rather stay with feisty.
By the way, I hose my laptop again (I don-t know if I should cry or laugh), ...
So I-m back in the club xD
Cheers
Luis

---

### Post by ASD2003ru on 2007-10-11
Heh... I create DTDS and apply. Sound work but how view temp of GPU and CPU and fans.
acpi -V  say 50-58C. 

In Windows fans work more often and them it is audible.

PS. Sorry, my english is bad :(

---

### Post by gene6482 on 2007-10-11
> **ASD2003ru said:**
> Heh... I create DTDS and apply. Sound work but how view temp of GPU and CPU and fans.
acpi -V  say 50-58C. 


Are you using Feisty or Gutsy

---

### Post by ASD2003ru on 2007-10-11
> **gene6482 said:**
> Are you using Feisty or Gutsy
Festy

PS. Toshiba p100-387 PSPA3E Bios 3.8

---

### Post by gene6482 on 2007-10-11
it works fine in feisty, but not in gutsy.

---

### Post by Tyriel on 2007-10-11
> **LuisC-SM said:**
> Nah....
Before I boot ACPI=off I rather stay with feisty.
By the way, I hose my laptop again (I don-t know if I should cry or laugh), ...
So I-m back in the club xD
Cheers
Luis

Same here which is a real shame as I am loving everything about Gutsy.  Still the only reason I point that out is that I think the issue may be in ther kernal ACPI code that must hve been changed.  What do you guys think?

Oh and I also broke my installation trying different methods out.  :(

---

### Post by ASD2003ru on 2007-10-12
> **gene6482 said:**
> it works fine in feisty, but not in gutsy.

I read somewhere that this problem is the kernel. 
The new kernel does not support a patch from / etc / initramfs-tools.
(Maybe in Gutsy only..)

---

### Post by LuisC-SM on 2007-10-13
> **Tyriel said:**
> Same here which is a real shame as I am loving everything about Gutsy.  Still the only reason I point that out is that I think the issue may be in ther kernal ACPI code that must hve been changed.  What do you guys think?
Well, it's all well known that this is a development distro, trying it  before the final release gives the developers a chance to enhance and bugfix everything. So I'll not complain about it. 
I'v been suscribed to the acpi ML for quite a while and they really have a hard work with laptops, especially toshiba. Toshiba itself is a devil, I think (sorta) they are cooperating to not use their machines under linux. I love toshiba, but for me, this was my last one. I'm thinking in buying a Lenovo and stay there for quite a while

> Oh and I also broke my installation trying different methods out.  :(
Welcomeback to the club  :guitar:
Right now, I'm using and old toshiba with xubuntu dapper, I must wait for my new hard disk for my p105-sp921,  broken on my last try :D

Luis

---

### Post by ozantabak on 2007-10-13
i dont even know how to upgrade my bios. can anybody help?

i have a satellite p100-219... i have the same sound problem....

---

### Post by zxc555_ on 2007-10-13
--------------------------------------------------------------------------------

thank you 
:confused:

---

### Post by LuisC-SM on 2007-10-13
> **ozantabak said:**
> i dont even know how to upgrade my bios. can anybody help?

i have a satellite p100-219... i have the same sound problem....

You must go to the Toshiba site and download the corresponding bios of your laptop model. 
Normally, the first time you start your computer, Toshiba asks you about your model and all thoses things you normally see to register your product. One of those things you must choose is to be noticed about updates. i f you did not do it, I suggest you to do it so you get mails every once (most of them useless but...) in a while, and sometime you will get a BIOS update/upgrade. (this is the first step you mus do in order to get help)
By the way, what's your BIOS version?
Cheers 
Luis

---

### Post by Tyriel on 2007-10-17
> **LuisC-SM said:**
> Well, it's all well known that this is a development distro, trying it  before the final release gives the developers a chance to enhance and bugfix everything. So I'll not complain about it. 
I feel the same way and I hope my little rant did not sound like a real complaint.  I love the hard work all the linux/ubuntu developers and community put into this fantastic operating system.

> **LuisC-SM said:**
> I'v been suscribed to the acpi ML for quite a while and they really have a hard work with laptops, especially toshiba. Toshiba itself is a devil, I think (sorta) they are cooperating to not use their machines under linux. I love toshiba, but for me, this was my last one. I'm thinking in buying a Lenovo and stay there for quite a while
Yea I am feeling the same way, after viewing the bios coupled with the troubles I have had I am a little disappointed with Toshiba.  Toshiba laptops are a fantastic product but I would much rather have a system that is Linux friendly. 

> **LuisC-SM said:**
> Welcomeback to the club  :guitar:
Right now, I'm using and old toshiba with xubuntu dapper, I must wait for my new hard disk for my p105-sp921,  broken on my last try :D

Luis

Back to running feisty currently but will try out Gutsy again soon and I hope a fix will be found soon.  Wish I had some time to play with the kernel code but I have too much work until next month :(

---

### Post by LuisC-SM on 2007-10-17
> **Tyriel said:**
> 
Back to running feisty currently but will try out Gutsy again soon and I hope a fix will be found soon.  Wish I had some time to play with the kernel code but I have too much work until next month :(

Hi Tyrel
I'm now running Gutsy on my 2nd partition waiting for the final kernel (I'm praying we will get a new one)  Everything is ok with my Feisty box (in fact I'm running "ComFusion" not quite feisty but a very nice and polished distro) I will not modify my gutsy install untill a see a new kernel version, in the meantime, I will play a little bit to see what else is not working.
Cheers
Luis

PS1. I omit to say that my old HD was broken thanks to me and not ubuntu :D
PS2. Right in [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469") (almost at the end, someone gave an idea about how mandriva guys had fixed this issue, I wen to the forums and found really nothing different than we we have been trying, if someone has a better luck than me, I'll appreciate any info.

---

### Post by ASD2003ru on 2007-10-19
New Ubuntu is out. Who tried to put something? Bug left?

---

### Post by paddyS on 2007-10-19
Not sure about the bios version on this one but just loaded up the new release (boot from CD - not installed) and no sound....

The good news it that it does now detect the rest of the hardware that it had problems with.... incl the geforce go760es0 and the PCI bridge that I had loads of grief with when I tried dapper a few months ago....

Haven't investigated further yet... I may give this another go!

---

### Post by LuisC-SM on 2007-10-19
I'm definitely moving to opensuse 10.3 and will continue using feisty.
This bug really sucks!!!

---

### Post by rzrgenesys187 on 2007-10-21
Sadly this fix no longer works in gutsy.

---

### Post by sw_ on 2007-10-21
the final release is out sooo... where's the fix?

is it really that hard to fix sich a basic thing as a sound card? - i mean the whole 3D eyecandy works like a charm but i can't listen to music or watch a movie i it... i don't think that's the way an operating system should be...

---

### Post by LuisC-SM on 2007-10-21
Hi folks... it'sme again.. :D

Well, I've installed Mandriva 2008.0 The free version) and I have sound :guitar: 
I posted in mandriva fourms my problem but I fixed it so easy :)
Take a look at my post and at the end there is the solution (check my *dmesg* file to see the bugs)
Cheers...
Link here: [http://forum.mandriva.com/viewtopic.php?p=386673#386673](http://forum.mandriva.com/viewtopic.php?p=386673#386673)
Luis.

PS: What I did was to add **[COLOR="Red"]acpi_osi=!Linux[/COLOR]** in the kernel boot parameters and THAT made the trick... Someone should try this in ubuntu and post here the results :D

---

### Post by ASD2003ru on 2007-10-21
> **LuisC-SM said:**
> Hi folks... it'sme again.. :D

Well, I've installed Mandriva 2008.0 The free version) and I have sound :guitar: 
I posted in mandriva fourms my problem but I fixed it so easy :)
Take a look at my post and at the end there is the solution (check my *dmesg* file to see the bugs)
Cheers...
Link here: [http://forum.mandriva.com/viewtopic.php?p=386673#386673](http://forum.mandriva.com/viewtopic.php?p=386673#386673)
Luis.

PS: What I did was to add **[COLOR="Red"]acpi_osi=!Linux[/COLOR]** in the kernel boot parameters and THAT made the trick... Someone should try this in ubuntu and post here the results :D

Heh.... if try acpi_osi=!Linux in Gypsy its work? Mey be kernel Madriva=Kernel Ubuntu?
In weekly i install new Ubuntu... and try this... if work, i write to topic.

---

### Post by LuisC-SM on 2007-10-21
> **ASD2003ru said:**
> Heh.... if try acpi_osi=!Linux in Gypsy its work? Mey be kernel Madriva=Kernel Ubuntu?
In weekly i install new Ubuntu... and try this... if work, i write to topic.
I'm NOT sure if this will work in ubuntu
I have 2.6.22.9 kernell in madriva, in fact, my kernel in mandriva is: **2.6.22.9-laptop-1mdv**, so as you can see it seems to be a special kernel for laptops, but you can give it a go i you wish.
Good luck
Luis

PS To me, the kernell version seems to be very alike (similar) to ubuntu's one.

---

### Post by numbers1thru9 on 2007-10-21
everything worked beautifully right out of the box with gutsy, the video and even the wireless!!! the only pain in the *** is the damn sound doesnt work and this fix doesnt work with gutsy, has anyone been able to get sound to work with gutsy yet? its driving me crazy cause i dont want to use vista anymore. PLEASE HELP!!!!!

---

### Post by Tyriel on 2007-10-23
> **LuisC-SM said:**
> Hi folks... it'sme again.. :D

Well, I've installed Mandriva 2008.0 The free version) and I have sound :guitar: 
I posted in mandriva fourms my problem but I fixed it so easy :)
Take a look at my post and at the end there is the solution (check my *dmesg* file to see the bugs)
Cheers...
Link here: [http://forum.mandriva.com/viewtopic.php?p=386673#386673](http://forum.mandriva.com/viewtopic.php?p=386673#386673)
Luis.

PS: What I did was to add **[COLOR="Red"]acpi_osi=!Linux[/COLOR]** in the kernel boot parameters and THAT made the trick... Someone should try this in ubuntu and post here the results :D


Thanks for the tip Luis, I'll give it a try in the next couple of days and let you know how it goes.

---

### Post by LuisC-SM on 2007-10-23
> **Tyriel said:**
> Thanks for the tip Luis, I'll give it a try in the next couple of days and let you know how it goes.

One more thing....
I've installed openSuSE 10.3 GNOME CD and Addons from [www.pcc-systems.com](www.pcc-systems.com).
I used the same fix (acpi_osi=!Linux) and guess what... **[COLOR="Red"]sound WORKS[/COLOR]** !!!! (Kernel 2.6.22.9-0.4-default)

So for me this is enough testing. 2 distros against 1... the winner is....

However, I'll keep on coming to this forum to see if devels have already charged the batteries :lolflag:

Good luck guys

Luis

---

### Post by Tyriel on 2007-10-24
Well I am going the upgrade to Gutsy now to try this out.  I'll let you know how it turns out.

---

### Post by ASD2003ru on 2007-10-24
For quick bugtrac: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

---

### Post by numbers1thru9 on 2007-10-24
I have installed the latest alsa drivers according to the instructions in the first post of this thread. I have also installed the custom DSDT.aml file after I compiled it from the .asl file and i even inserted the acpi_osi=!Linux to the boot options as I was getting that same error in my dmesg as the other guy. However I still cannot get sound unless I pass the acpi=off option to the kernel at boot. My laptop is a P105-S6177 running gutsy BIOS version 3.30 but will upgrade to 3.80

---

### Post by ASD2003ru on 2007-10-24
Madriva Powerpack 2008 worked. Without acpi_osi=!Linux.

---

### Post by Tyriel on 2007-10-24
Unfortunately (acpi_osi=!Linux) did not work for me either.  However the comments in the bugtrac that  ASD2003ru posted seem very promising. (fingers crossed!)

I might try another distribution in the mean time keeping a close eye on a fix for this issue.

---

### Post by gene6482 on 2007-10-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+s...22/+bug/136469](https://bugs.launchpad.net/ubuntu/+s...22/+bug/136469) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				sadly, i've switched to mandriva for the time being. I definitely like Ubuntu better, but sound is a deal-breaker for me. I tried to wipe the machine and go back to feisty, but I forgot how I got the sound working the first time, and couldn't get it back to where i had sound. Hopefully the bug gets fixed and i can come back.

Bye for now.

---

### Post by rzrgenesys187 on 2007-11-29
Gutsy sound fix (from: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469))

follow the steps in the first post of this thread to get the custom dsdt file and afterwards do this: (info reprinted from Brint E. Kriebel's post)

-download [http://fragglenet.com/tools/toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz](http://fragglenet.com/tools/toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz)
-open Terminal and enter this commands :
```

tar xvf toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz
cd toshiba_dsdt_kernel_fix.2.6.22-14_2007111300/
dpkg -i *.deb
```
-reboot

---

### Post by LuisC-SM on 2007-11-29
Good Job!!!!
Thanks

Luis

---

### Post by ASD2003ru on 2007-11-30
Good message .
However, I have already put Mandriva in which it works. And see no sense in all of these fixes. With each change of the kernel such anguish ... 

PS. Maybe read that even with the Ubuntu laptop HDD skew work?

---

### Post by octesian on 2008-01-05
> **rzrgenesys187 said:**
> Gutsy sound fix (from: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469))

follow the steps in the first post of this thread to get the custom dsdt file and afterwards do this: (info reprinted from Brint E. Kriebel's post)

-download [http://fragglenet.com/tools/toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz](http://fragglenet.com/tools/toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz)
-open Terminal and enter this commands :
```

tar xvf toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz
cd toshiba_dsdt_kernel_fix.2.6.22-14_2007111300/
dpkg -i *.deb
```
-reboot

Unfortunately that only works for 32 bitsystems.  This problems a huge pain for amd64 :(

---

### Post by octesian on 2008-01-08
Well I switched back to gutsy 386.  The sound fix works great but the GPU fan doesnt work.  It spins sometimes when I'm not using the nvidia driver but doesnt seem to spin at all.  I read that appearantly the CPU and GPU fans are somewhat linked and that the GPU fan was controlled by the Windows driver.  I'm currently investigating a DSDT fix to have the fans running at all times but I dont know if I'll be able to do it.

Edit:  Oh yeah, I've got a p105-s9337 with bios 4.2

---

### Post by LuisC-SM on 2008-01-09
@octesian

To fix the fan problem in your dsdt file, just insert this line:
**[COLOR="Blue"]Store (0x50, VTMP) // Credit goes for Martin Lorang[/COLOR]**
in the **Method (_REG, 2, NotSerialized) (at the end)** before the last curly brace.
So it should look something like this:
```
Method (_REG, 2, NotSerialized)
                    {
                        If (LEqual (Arg0, 0x03))
                        {
                            Store (Arg1, Local0)
                            If (Local0)
                            {
                                Store (0x01, ECOK)
                                Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
                                Store (\TMOD, \_SB.PCI0.LPCB.EC0.TMOD)
                                Release (\_SB.PCI0.LPCB.EC0.MUT1)
                            }
                            Else
                            {
                                Store (0x00, ECOK)
                            }
                        }

                        If (\_SB.ECOK)
                        {
                            Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
                            If (LEqual (OSYS, 0x07D6))
                            {
                                Store (One, \_SB.PCI0.LPCB.EC0.OSTP)
                                \_SB.PHSR (0x0D, 0x00)
                            }
                            Else
                            {
                                Store (Zero, \_SB.PCI0.LPCB.EC0.OSTP)
                            }

                            Store (0x03, \_SB.PCI0.LPCB.EC0.RG59)
                            Store (\_SB.CIRE, \_SB.PCI0.LPCB.EC0.CIRE)
                            Store (\_SB.PHSR (0x05, 0x00), DOFF)
                            Store (\_SB.PCI0.LPCB.EC0.ACDF, \PWRS)
                            Release (\_SB.PCI0.LPCB.EC0.MUT1)
                        }
			// Martin Lorang's hack
			
			  Store (0x50, VTMP) // 55°C avec glxgears, 48°C au repos, temp ext 24°C
                    }

```

Cheers

Luis

---

### Post by octesian on 2008-01-09
That is soo.... :cry: I love you man!  I've been picking apart my DSDT for the past 3 days trying to get it to work.  Thank you!

---

### Post by LuisC-SM on 2008-01-09
You r welcome.
Other values you can use (higher).... just to compare...
> Store (0x30, VTMP) // 72°C avec glxgears, 65°C au repos, temp ext 24°C
			Store (0x3C, VTMP) // 60°C con glxgears, 52°C en reposo, temp ext 24°C
			Store (0x46, VTMP) // 55°C con glxgears, 50°C en reposo, temp ext 24°C
Cheers

Luis

---

### Post by anthony.canucks on 2008-01-18
I am having problems with the sound as well. I managed to get it working using this guide [http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html](http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html) along with acpi=off. The problem is that ubuntu still stops responding after a few minutes (it did this before I fixed the sound as well). I think that it's because of my gpu fan not working properly (I tried the fix posted above).

any ideas on how to get sound and have ubuntu working properly?

---

### Post by LuisC-SM on 2008-01-19
@Anthony

What model of Toshiba do u have?
If you have a P100/105 series, why don't u try tupgrading to BIOS 4.20, I just did it and I had no single problem with sound. 

Right now, I've just installed Mandriva 2008.1 (cooker) and I did'nt even had to use the ACPI table (DSDT), sound came just right out of the box with kernel 2.6.24

I'm using ubuntu Hardy Heron Alpha 3 and sound is ok working with a fixed DSDT

Cheers.

Luis

---

### Post by anthony.canucks on 2008-01-21
P100

I have the 4.20 bios. 

I got the sounds working with the fixed DSDT and ACPI off but ubuntu is still freezing.

---

### Post by octesian on 2008-01-23
Heres what I used too get mine to work (and it works flawlessly);

This was taken from a post at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469")

> 
The process was:
1. Update my bios to v4.2
2. Download a kernel fix from [http://fragglenet.com/tools/toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz]("http://fragglenet.com/tools/toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz")
3. Fix dsdt for nvidia temperature using instructions at [http://www.linuxforums.org/forum/newreply.php?do=newreply&noquote=1&p=477653]("http://www.linuxforums.org/forum/newreply.php?do=newreply&noquote=1&p=477653")

Dont forget to add the line from LuisC-SM's post. After copying your new DSDT.aml to /etc/initramfs-tools/ run the command 
> 
sudo update-initramfs -u -k `uname -r`

> 
4. Open Terminal and enter these commands:
* tar xvf toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz
* cd toshiba_dsdt_kernel_fix.2.6.22-14_2007111300/
* dpkg -i *.deb
5. Reboot computer and enjoy.
6. Use "Envy" from [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") to configure the latest Nvidia drivers for this computer


Unfortunately this only works for Gutsy I386 and I havent been able to find a kernel fix for amd64.

---

### Post by LuisC-SM on 2008-01-23
@Octesian
Thanks for your comment. I think that's all to be done.

@Anthony
You don't need to boot with acpi=off, if you have already fixed your table (DSDT) then boot acpi ON, (that's the reason why you have fixed it).

Another trick is to boot with the **acpi_osi=!Linux** parameter, this could help you a lot I believe. But don't turn ACPI=OFF please)

Cheers

Luis

---

### Post by ArmandoXIII on 2008-01-28
Guys, help me please, I found the file Kaass uploaded, but it doesn't contain said .aml file, anyone has it???

---

### Post by anthony.canucks on 2008-01-29
Seems to working fine now. Thanks a lot.

---

### Post by LuisC-SM on 2008-01-29
> **ArmandoXIII said:**
> Guys, help me please, I found the file Kaass uploaded, but it doesn't contain said .aml file, anyone has it???

Armando, can you explain a little bit more what's your problem?.. I really don't understand anything of what you have just written and most probabily neither one of other members too.

Regards.

Luis

---

### Post by ArmandoXIII on 2008-01-30
Nevermind the TCs dsdt.aml file, here is my problem,

I'm using Kubuntu 7,10

I just decompiled, fixed and recompiled my own dsdt, then i put it in "/etc/initramfs-tools/DSDT.aml" and did the "sudo dpkg-reconfigure linux-image-$(uname -r)", rebooted, but still no sound, i also added acpi_osi=!Linux to the menu.lst, but still doesn't work, anyone can help me?

---

### Post by ArmandoXIII on 2008-01-30
BTW My laptop model is Toshiba P105 S6227, my sound card is Conexand HD Audio, please help me i'm almost crying here.

---

### Post by ArmandoXIII on 2008-01-30
> **octesian said:**
> Heres what I used too get mine to work (and it works flawlessly);

This was taken from a post at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469")


Dont forget to add the line from LuisC-SM's post. After copying your new DSDT.aml to /etc/initramfs-tools/ run the command 



Unfortunately this only works for Gutsy I386 and I havent been able to find a kernel fix for amd64.

THANK YOU! the kernelfix worked, oh my god, thank you so much :D

---

### Post by geopgeop on 2008-02-07
> **octesian said:**
> Heres what I used too get mine to work (and it works flawlessly);

This was taken from a post at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469")


Dont forget to add the line from LuisC-SM's post. After copying your new DSDT.aml to /etc/initramfs-tools/ run the command 



Unfortunately this only works for Gutsy I386 and I havent been able to find a kernel fix for amd64.
Will this also work with Ubuntu Studio's realtime kernel (-rt)?

---

### Post by octesian on 2008-02-14
I have no idea, sorry :(  I've only tested it in plain ubuntu.  If you want to try it, I'm sure others would like to know your results.

---

### Post by gene6482 on 2008-02-15
i'm not sure about ubuntu studio, but with hardy alpha, it works fine.

---

