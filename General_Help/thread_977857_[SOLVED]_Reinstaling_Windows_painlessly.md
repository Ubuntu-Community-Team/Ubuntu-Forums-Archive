---
title: "[SOLVED] Reinstaling Windows painlessly"
date: 2008-11-10
forum: General Help
---

### Post by fiddler616 on 2008-11-10
Hello,
I've been quite happy with my dual-boot--Ubuntu for everything, Windows just-in-case, until XP decided it wanted SP3. It started downloading/installing...when it told me it had run out of disk space. So I cancelled it, grew the partition, went back into Windows...and it [wouldn't load all the way]("http://ubuntuforums.org/showthread.php?p=6137776#post6137776"). A guru at school said the only good way to fix it was reinstalling Windows. Whatever--I don't have anything that important on it.
But reinstalling Windows overwrites GRUB, which is a problem.[URL="http://ubuntuforums.org/showthread.php?p=6103826#post6103826"]
I've unsuccessfully tried this in the past[/URL], and it was--in a word--unsuccesfull.

So I'm a little bit unsure about what to do.

I made /home a separate partition--and it's the one with all my important files, so I guess I could just reinstall Ubuntu after Windows and tell it to use the existing /home partition (that *does* work, right?)

I don't really trust GRUB/menu.lst/SuperGRUBDisk anymore.

I have an external hard drive which is bigger than the internal--would it be worth my while to make an image (how?) of / and /home, and then restore it?

Thanks for any help/advice.

---

### Post by -Zeus- on 2008-11-10
so, what you want to do is go ahead and boot to the windows cd.  There should be a partition list somewhere in the install procedure, select the former windows partition for that.  Once you've installed, boot to a live cd, open a console, and type this:
```
sudo grub
grub> root (hdn,m)
grub> setup (hdn)
grub> exit
```

You can get the n,m values from sudo fdisk -l, if you can figure it out yourself, or else just post the output if sudo fdisk -l here and i'll tell you what to put in.

---

### Post by Idefix82 on 2008-11-10
> **-Zeus- said:**
> so, what you want to do is go ahead and boot to the windows cd.  There should be a partition list somewhere in the install procedure, select the former windows partition for that.  Once you've installed, boot to a live cd, open a console, and type this:
```
sudo grub
grub> root (hdn,m)
grub> setup (hdn)
grub> exit
```

You can get the n,m values from sudo fdisk -l, if you can figure it out yourself, or else just post the output if sudo fdisk -l here and i'll tell you what to put in.

+1. Reinstalling Windows is non-sense, you simply need to update grub.

---

### Post by fiddler616 on 2008-11-15
> **-Zeus- said:**
>  or else just post the output if sudo fdisk -l here and i'll tell you what to put in.
That's probably a good idea--the last thing I need is to think I know more than I do and screw something up.
```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         849     6819561   83  Linux
/dev/sda2             850        1824     7831687+  83  Linux
/dev/sda3            2762        2837      610470   82  Linux swap / Solaris
/dev/sda4   *        3862        4864     8056597+   7  HPFS/NTFS

``` 
(I don't understand how two numbers can come out of sda**4**)
Thank you very much.

---

### Post by caljohnsmith on 2008-11-15
Fiddler616, since you have two linux partitions, and since it isn't clear which one has your Grub files, how about trying this to reinstall Grub to your MBR (Master Boot Record):
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) as either (hd0,0) or (hd0,1), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands, reboot, and let me if you at least get a Grub menu on start up. :)

---

### Post by fiddler616 on 2008-11-15
> **caljohnsmith said:**
> Fiddler616, since you have two linux partitions, and since it isn't clear which one has your Grub files, how about trying this to reinstall Grub to your MBR (Master Boot Record):
```
sudo grub
grub> find /boot/grub/stage1
```The command above should return your main Ubuntu partition in the form of (hdX,Y) as either (hd0,0) or (hd0,1), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit
```Please post the output of all the above commands, reboot, and let me if you at least get a Grub menu on start up. :)
Thanks.
```
grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0, 0)

Error 11: Unrecognized device string

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


```
FYI, when I first typed in sudo grub, it gave me a line about "probing the BIOS for device drives, this might take a long time"
I'm gonna reboot now--I'm just taking advantage of a LiveCD with authenticated WLAN, open Firefox, open thread in FF, etc.

---

### Post by fiddler616 on 2008-11-15
Coolio, I'm in my old Ubuntu install!!
However, doing Windows leads to
> Error 13: Invalid or unexecutable format
CarlJohnSmith--this is beginning to sound like the thread we already had, where I added Windows boot files with a zip you gave me....

---

### Post by SunnyRabbiera on 2008-11-15
the best way to install windows painlessly is to get gallons and gallons of Novocaine :D

---

### Post by fiddler616 on 2008-11-15
> **SunnyRabbiera said:**
> the best way to install windows painlessly is to get gallons and gallons of Novocaine :D
I should've gotten some before being forced to write this blog post:[http://tmac.andrewmin.com/blog/?p=95](http://tmac.andrewmin.com/blog/?p=95)

---

### Post by caljohnsmith on 2008-11-15
> **fiddler616 said:**
> 
CarlJohnSmith--this is beginning to sound like the thread we already had, where I added Windows boot files with a zip you gave me....
Yes, this feels like Deja Vu, doesn't it? Oh well, hopefully it won't be a big deal to get your Windows booting this time. Sounds like you just need the correct Grub entry for Windows, so how about pulling up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And your Windows entry should look like:
```
title Windows XP 
root (hd0,3)
chainloader +1
```
Reboot, and I'm guessing that will be all it takes to boot Windows. If not, let me know how far you get. :)

---

### Post by fiddler616 on 2008-11-15
> **caljohnsmith said:**
> Yes, this feels like Deja Vu, doesn't it? Oh well, hopefully it won't be a big deal to get your Windows booting this time. Sounds like you just need the correct Grub entry for Windows, so how about pulling up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```And your Windows entry should look like:
```
title Windows XP 
root (hd0,3)
chainloader +1
```Reboot, and I'm guessing that will be all it takes to boot Windows. If not, let me know how far you get. :)
Hoo boy.
OK, first, let me explain the mess that is my Windows boot menu (not GRUB, Windows' boot loader)
There was an entry called "Windows XP" from the start. Don't ask--I don't know.
Last week's install made "Windows XP Home Edition" which obviously doesn't boot, since the partition no longer exists.
This week's (boy, that doesn't come out right) Windows added another "Windows XP Home Edition", which is the default, and is the one I used before restoring GRUB.
All three of them now display something along the lines of missing file: hal.dll missing or corrupted.
Curses.

Thanks for your help though!

---

### Post by fiddler616 on 2008-11-15
Just for the record, I went through the steps you (Carljohnsmith) described in the other thread about mounting the Windows partition and listing the files, and all the boot files are there. But I kinda thought they would be--since it wasn't raising the NTLDR error.
Just for the record.

---

### Post by caljohnsmith on 2008-11-15
OK, that "missing hal.dll" error usually means your boot.ini file is pointing to the wrong partition, so it makes it look like the hal.dll file is missing, when really it isn't. I modified a boot.ini file so that it should work with your Windows being on sda4, so go ahead and download "boot.ini.txt" to your desktop, and do:
```
sudo mount /dev/sda4 /mnt
sudo cp /mnt/boot.ini /mnt/boot.ini.backup
sudo mv ~/Desktop/boot.ini.txt /mnt/boot.ini

```
Reboot, and let me know how far you get booting Windows. :)

---

### Post by fiddler616 on 2008-11-15
> **caljohnsmith said:**
> OK, that "missing hal.dll" error usually means your boot.ini file is pointing to the wrong partition, so it makes it look like the hal.dll file is missing, when really it isn't. I modified a boot.ini file so that it should work with your Windows being on sda4, so go ahead and download "boot.ini.txt" to your desktop, and do:
```
sudo mount /dev/sda4 /mnt
sudo cp /mnt/boot.ini /mnt/boot.ini.backup
sudo mv ~/Desktop/boot.ini.txt /mnt/boot.ini

```Reboot, and let me know how far you get booting Windows. :)
OK, I noticed two things:
*The boot menu shows XP, of course, and something that begins with /fastdetect
*Windows hangs at the blue splash screen, like it did here: [http://ubuntuforums.org/showthread.php?t=976440](http://ubuntuforums.org/showthread.php?t=976440)

---

### Post by caljohnsmith on 2008-11-15
> **fiddler616 said:**
> OK, I noticed two things:
*The boot menu shows XP, of course, and something that begins with /fastdetect
*Windows hangs at the blue splash screen, like it did here: [http://ubuntuforums.org/showthread.php?t=976440](http://ubuntuforums.org/showthread.php?t=976440)
OK, I didn't realize your Windows was so far gone. So I assume from your blog post that you don't have your Windows Install CD? You did say you have your Windows product key or whatever Microsoft calls it, right? If so, you could just torrent a Windows Install CD and use it with your legitimate product key. I would try doing a "Windows Repair" from the Install CD before totally reinstalling, but it's up to you. And don't worry at all about overwriting Grub in the MBR, just follow the steps from your post #6 to reinstall Grub if necessary. Good luck and let me know how it goes.

---

### Post by fiddler616 on 2008-11-15
> **caljohnsmith said:**
> OK, I didn't realize your Windows was so far gone. So I assume from your blog post that you don't have your Windows Install CD? You did say you have your Windows product key or whatever Microsoft calls it, right? If so, you could just torrent a Windows Install CD and use it with your legitimate product key. I would try doing a "Windows Repair" from the Install CD before totally reinstalling, but it's up to you. And don't worry at all about overwriting Grub in the MBR, just follow the steps from your post #6 to reinstall Grub if necessary. Good luck and let me know how it goes.
Eek, so that we're clear, the thread I linked to was a previous XP install, that I've since gotten rid of for the current one. It's completely fresh except I:
Installed Firefox, Sony drivers, and SP2.

Otherwise....darn....

I looked into a bootleg XP torrent once, except I had a bit of trouble, everything was either:
"enhanced" in some piratical way, which I did not desire
OEM disk for an OEM that isn't mine.
.rar file, not .iso

If you think I should look harder, I'll go right ahead though.

---

### Post by caljohnsmith on 2008-11-15
OK, so can you summarize for me what exactly happened? If your current install is fresh, how did you install it without a Windows Install CD? Is the current situation that Windows ran out of disk space when installing SP3, and since then it gives you a blue screen? If that's true, sounds like you either need to make the Windows partition larger and reinstall (since you will have to expand the beginning of its partition, not end), or you would have to delete some of your files in Windows and do the "Windows Repair" option.

---

### Post by fiddler616 on 2008-11-15
> **caljohnsmith said:**
> OK, so can you summarize for me what exactly happened? If your current install is fresh, how did you install it without a Windows Install CD? Is the current situation that Windows ran out of disk space when installing SP3, and since then it gives you a blue screen? If that's true, sounds like you either need to make the Windows partition larger and reinstall (since you will have to expand the beginning of its partition, not end), or you would have to delete some of your files in Windows and do the "Windows Repair" option.
Sorry for any confusion.

I reinstalled Windows last week, it had issues with SP3, hung upon bootup, and is gone. You can safely stop thinking about it.

I reinstalled Windows yesterday, installed the few programs I said, restored GRUB, fixed boot.ini, and am having trouble with the exact same hanging phenomenon--which I think is kinda weird since it's a completely separate install/partition/everything.

The way I reinstalled it was with a thingy called BartPE. It provides a LiveCD with a very rudimentary Windows envorionment, from which I ran C:\Windows\i386\winnt32.exe
That's the Windows Setup program, and from it I was able to install Windows.

I hope that explains everything--I can elaborate if you want me to, but it seemed like less is more in this particular case.

Thanks.

---

### Post by caljohnsmith on 2008-11-15
> **fiddler616 said:**
> 
I reinstalled Windows yesterday, installed the few programs I said, restored GRUB, fixed boot.ini, and am having trouble with the exact same hanging phenomenon--which I think is kinda weird since it's a completely separate install/partition/everything.

After you reinstalled Windows with BartPE, were you able to boot into it a couple of times OK? Was it only after you installed those few programs that you get a BSOD on rebooting? I'm not sure how close that BartPE install is to a genuine Windows install from the Windows Install CD, but that could be a likely cause of your Windows BSOD.

---

### Post by fiddler616 on 2008-11-15
> **caljohnsmith said:**
> After you reinstalled Windows with BartPE, were you able to boot into it a couple of times OK? Was it only after you installed those few programs that you get a BSOD on rebooting? I'm not sure how close that BartPE install is to a genuine Windows install from the Windows Install CD, but that could be a likely cause of your Windows BSOD.
Yeah, everything worked great, I 'Validated' it, I rebooted quite a few times, etc.
The only problem came from after restoring Ubuntu...

From what I understand, all BartPE does is provide an environment to run winnt32.exe from--which is a legitimate Microsoft program.

---

### Post by caljohnsmith on 2008-11-15
> **fiddler616 said:**
> Yeah, everything worked great, I 'Validated' it, I rebooted quite a few times, etc.
The only problem came from after restoring Ubuntu...

How did restoring Ubuntu affect your Windows partition? What did you do to restore Ubuntu? So are you saying your Windows still worked fine after installing Firefox, Sony drivers, and SP2, but after restoring Ubuntu, Windows now BSODs?

---

### Post by fiddler616 on 2008-11-15
> **caljohnsmith said:**
> How did restoring Ubuntu affect your Windows partition? What did you do to restore Ubuntu? So are you saying your Windows still worked fine after installing Firefox, Sony drivers, and SP2, but after restoring Ubuntu, Windows now BSODs?
That's exactly what I'm wondering.
Restoring Ubuntu consisted of this thread--recovering GRUB, boot.ini, etc.
Even though it's a blue screen of death, it's not *the* BSOD--if it were Ubuntu I'd called it the splash screen while the GDM was loading--if you know what I mean.

---

### Post by caljohnsmith on 2008-11-15
Well since your Windows is a relatively fresh install, how about reinstalling Windows, making sure Windows boots successfully, reinstall Grub, and then make sure you can still boot Windows from Grub; after that try adding your programs, drivers, SP2/SP3, etc to Windows. That's about my only suggestion at this point, because I don't understand what happened to cause Windows to BSOD.

---

### Post by fiddler616 on 2008-11-15
> **caljohnsmith said:**
> Well since your Windows is a relatively fresh install, how about reinstalling Windows, making sure Windows boots successfully, reinstall Grub, and then make sure you can still boot Windows from Grub; after that try adding your programs, drivers, SP2/SP3, etc to Windows. That's about my only suggestion at this point, because I don't understand what happened to cause Windows to BSOD.
OK, sounds good. I'll try it tomorrow though--it's almost midnight here, and sleep is always fun....
To restore GRUB I'll just start at the beginning of this thread, right?

---

### Post by caljohnsmith on 2008-11-15
> **fiddler616 said:**
> OK, sounds good. I'll try it tomorrow though--it's almost midnight here, and sleep is always fun....
To restore GRUB I'll just start at the beginning of this thread, right?
Just doing what you did in post #6 should do the trick. Good luck and let me know how it goes when you get around to doing it. :)

---

### Post by fiddler616 on 2008-11-16
Windows reinstalled. As soon as it loaded everything, I immediately restarted into my Intrepid LiveCD.

```
grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


```
Now I'm rebooting, goodbye, sweet live environment!

---

### Post by fiddler616 on 2008-11-16
Sweet!
I am now a dual-booter!
Thanks to everybody!
(I'm assuming that installing updates/drivers in Windows is going to work without a hitch...stranger things have happened though)
But for now, I'm basking in the glow of my GRUB menu.

<Solved> (OK, maybe it wasn't painlessly, but it could've been a lot harder)

---

### Post by TeXtonyx on 2008-11-16
You need to be careful about installing SP3, like turning off the
anti-virus program. MS provides warnings about what not to do
at their website.

---

### Post by fiddler616 on 2008-11-16
> **TeXtonyx said:**
> You need to be careful about installing SP3, like turning off the
anti-virus program. MS provides warnings about what not to do
at their website.
Good call, thanks.

---

