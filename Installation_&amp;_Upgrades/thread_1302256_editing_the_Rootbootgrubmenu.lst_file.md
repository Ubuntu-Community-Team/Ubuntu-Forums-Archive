---
title: "editing the Root/boot/grub/menu.lst file"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by gride on 2009-10-26
hello this is my first post here
i just installed kubuntu 9.04 on a its own partition on a drive separate from my xp os. i followed some of the directions posted on the forums and it seemed to work nicely.
now i've plugged my xp drive back in on sata channel 2 (two sata drives)
i am trying to edit the menu.lst file so i can choose which os to boot at startup.
it opens in Kate (included text editor) but wont let me save the file 
it seems to have permissions requirements for the file
ive tried to change the permissions to no avail and think its time to throw in the towel and see if someone here has had a similar issue and may have the answer

ps this is my first linux experience and i think im gonna end up being a convert
great forums too:)

---

### Post by Rocket2DMn on 2009-10-26
In order to edit this file, you need sudo/root privileges.  You can read up on sudo here - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To edit the file with graphical sudo.  In Ubuntu we would use gksudo (or gksu), but since you are using Kubuntu, you would use:
```
kdesu kate /boot/grub/menu.lst
```
It is always good to make a backup of system files before modifying.  For this file, backup like so:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
That way in case you mess it up badly, you can simply restore the file:
```
sudo mv /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

---

### Post by gride on 2009-10-27
yeah thanks rocket
that sudo worked for being able to edit that file
the command i used was:
> kdesudo kate /root/boot/grub/menu.lst

i still got to play around with it to make it give my a boot options screen,
but that was the part i was stuck on till now
thanks again

---

