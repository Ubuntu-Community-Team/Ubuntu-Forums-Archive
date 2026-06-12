---
title: "Grub Broken at Boot Prompt"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by siriusfox on 2009-02-01
I went to boot back onto my Laptop today, and out of the blue it has stopped working.

When I boot, I get my normal BIOS screen, then I'm dumped to a boot command prompt. No errors that I can see, or any messages that are telling me what to do.

I've booted into live environments, and I've checked my menu.lst, and as far as I can tell it works. I've also tried calling
```
grub> root (hd0,4) # Meaning sda5 where Ubunu and my grub config is located
grub> setup (hd0)
```
with no errors. Everything runs smoothy.

also If at the prompt I run the following
```
grub> root (hd0,4)
grub> kernel /vmlinuz root=/dev/sda5 ro splash
grub> initrd /initrd.img
grub> boot
```
Then I can boot into Ubuntu without a hitch, but for whatever reason I can't get grub to show me the list at all. Any suggestions on how I might go about fixing this?

---

### Post by ratmandall on 2009-02-01
I recently had a grub f*** up, I tried several "fixes" which did not work so I just re-installed grub.

Boot into the ubuntu live cd.
And enter these commands in the terminal
```
$sudo grub
$find /boot/grub/stage1
$root (hd0,0) #Replace "(hd0,0)" with the string that the above command returned.
$setup (hd0)

```
Reboot
????
Hopefully profit :p

EDIT:O I see you already tried that #-o

---

### Post by siriusfox on 2009-02-01
I'm attaching a copy of my menu.lst file. I just noted that if I type configfile /boot/grub/menu.lst then my prompt is cleared except for the header that shows up when I start. My only thought now is my configuration done wrong, but no errors are showing up so I don't know.

---

### Post by caljohnsmith on 2009-02-01
Siriusfox, how about trying the following while you are in your sdb5 Ubuntu install:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install /dev/sda
```
And please post the output of all the above commands. If they complete successfully, try rebooting and see if you get the Grub menu yet. If not, how about booting into Ubuntu again, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by siriusfox on 2009-02-01
No Errors on the purge/install. The output of grub-install is as follows.
```
Searching for GRUB installation directory ... found: /boot/grub
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map
Check if this is correct or not. If any of the lines is incorrect
fix it and re-run the script `grub-install`

(hd0)     /dev/sda
```
Then I'm given a prompt.

Upon reboot I'm given the exact same grub prompt with no menu. So I did a manual boot again and downloaded the bootinfoscript. The output is attached.

---

### Post by caljohnsmith on 2009-02-01
From the results of that script, it looks like everything is in order and you should get the Grub menu on start up. I didn't quite understand what you meant in your post #3 where you said:
> I just noted that if I type configfile /boot/grub/menu.lst then my prompt is cleared except for the header that shows up when I start.
What happens when you do:
```
grub> configfile (hd0,4)/boot/grub/menu.lst
```
at the Grub prompt now? Does it load your menu.lst? If not, does this show it:
```
grub> cat (hd0,4)/boot/grub/menu.lst
```
Also, when you boot into Ubuntu, please post:
```
ls -l /boot/grub/
```
And we can work from there.

---

### Post by siriusfox on 2009-02-01
configfile (hd0,4)/boot/grub/menu.lst did exactly what I said before. It clears any commands I had been typing at the grub prompt, and gives me the default grub boot prompt. This is different from the clear command, as it lacks the header information that I get upon first launching grub.

The odd thing though, is I did run cat (hd0,4)/boot/grub/menu.lst on my own before this, and it listed a handful of lines, each line being it's own boot entry, and all other options on one line after it. No settings or comments were visible.

I did note though, that when I was looking at the file in nano, it told me that it had to convert the file from the Mac. I did a quick search on changing Mac line endings to Unix line endings, and that corrected my problem.

Thanks for your help.

---

