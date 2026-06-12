---
title: "Please help me with my problem of dual boot"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by msrvenkat on 2009-01-06
I wanted to have dual boot option such that I have Ubuntu 8.10 and
windows . But during the install, I chose different hard  disk to use fully for this install. I have a C:drive and F:drive , basically two hard disks on my PC.
Now I do not see any option of going to Ubuntu after startup
it goes only to windows booting from C:
I did not see dual boot option on startup. 
Where did i mess up?  Please help

---

### Post by kixome on 2009-01-06
I have experienced this same problem when multi-booting.  Go into your bios and make sure it lists the ubuntu drive as the first boot device. If it doesn't not list as the 1st boot device, change the option.

Thats where I had messed up!

hope this helps.

---

### Post by msrvenkat on 2009-01-06
I dont know what happened but now after the start it says
grub failed , error 21 
Now I can neither boot windows nor Ubuntu
Someone please save me

---

### Post by Zeroberry on 2009-01-06
What did you change? Go into bios and make sure you have both hard drives enabled. The GRUB booter will say something like that if it can't access the ubuntu hard drive, I had a similar problem.

You could reinstall Ubuntu and make sure you get the master boot record right. Not an expert but that should do it.

---

### Post by caljohnsmith on 2009-01-06
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by TSellers on 2009-01-06
I'm having exactly the same problem. I tried first with new partitions on a WIndows Drive. No Luck. So then I installed an old 40GB drive which I used the whole thing for the Ubuntu partition and swap. But when I reboot nothing, just windows. Why does it not show up in the boot manager? Changing the drive in the BIOS doesn't seem to make sense.

---

### Post by kixome on 2009-01-06
I was just telling you what I did wrong. I had this exact same problem with my old computer.

When I got this error I pointed the bios to boot from the ubuntu drive, and then reinstalled Ubuntu. Wa-la it worked Like a charm. Anytime Windows continues to boot after installing Ubuntu, look to the bios first, and if that isn't the problem then you must not have installed the boot loader on the same drive that the bios boots to. i.e. the bios settings are usually, but not always incorrect.

---

### Post by kixome on 2009-01-06
> **TSellers said:**
> I'm having exactly the same problem. I tried first with new partitions on a WIndows Drive. No Luck. So then I installed an old 40GB drive which I used the whole thing for the Ubuntu partition and swap. But when I reboot nothing, just windows. Why does it not show up in the boot manager? Changing the drive in the BIOS doesn't seem to make sense.

In the IT field not everything seems to make sense, but that does not mean that it doesn't work.

---

### Post by TSellers on 2009-01-06
Sorry, I should have been more specific.

There is no option in my bios to chosse a particular drive. It is either "Hard Drive", "CD", "USB', LAN, etc.

THanks for the reply.

---

### Post by kixome on 2009-01-11
It sounds like grub is not installing properly,You can try this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) 

also, if you happen to mess up your xp boot loader and you cannot boot at all then: boot to xp cd. when booted select the repair and recovery by pressing r, follow the prompts until you reach the command line and then type: fixmbr and then fixboot and restart then xp should work fine again.
hope this helps!

---

