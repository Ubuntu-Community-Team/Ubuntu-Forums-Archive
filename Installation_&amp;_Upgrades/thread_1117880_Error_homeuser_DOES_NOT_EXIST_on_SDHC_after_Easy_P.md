---
title: "Error: /home/user DOES NOT EXIST on SDHC after Easy Peasy login"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by kallenes on 2009-04-06
Can someone help me on this one?

I've installed ubuntu's easy peasy on my 901. GNOME.

mounted as such:
sda ext2 / on the 4GB SSD
sdb ext3 /usr and /tmp on the 16GB SSD
sdc ext3 /home on a Kingston 8GB SDHC class 6
not using a swap

was running like a charm for over a week, when suddenly today on boot up after i login, i get the **ERROR /home/username DOES NOT EXIST**. then asks me to create it in the /root.
every session i try hangs before my desktop appears. except TERMINAL, which i can access.

i can see the USB FLASH entry in the BIOS.
i'm using a grub splashimage.

what have i done wrong? should i partition differently? how can i get /home working again on the SDHC? (i don't care about lossing data on the SDHC, i just want to avoid a fresh installation)

i've seen other post with similar issues .. but not exactly as i have.

Thanks

---

### Post by taurus on 2009-04-06
Does the 8GB drive get mounted when you boot your machine?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by kallenes on 2009-04-06
would i see if the drive gets mounted by hitting ESC at the grub?

---

### Post by taurus on 2009-04-06
Nope.  You have to wait for it to finish booting before you can view your harddrives.

---

### Post by kallenes on 2009-04-06
could catch the drive to see if was mounted, scrolling to fast. couldnt pause. im quite new to linux. sorry.

but what i saw in terminal 


sudo fdisk -l   [COLOR="Red"]sdc- my SD card was in the list[/COLOR]
sudo blkid       [COLOR="Red"]also listed[/COLOR]
cat /etc/fstab   [COLOR="Red"]not listed [/COLOR]
df -h            [COLOR="Red"]not listed[/COLOR]


btw: taurus thanks for your time

---

### Post by taurus on 2009-04-06
If it is not in /etc/fstab, then you need to add an entry in there for that 8GB drive, mounting to /home.  The entry in /etc/fstab for that drive, using UUID, would look something like

```
UUID=*abcd1234efgh5678*   /home   ext3   relatime   0   2
```
Of course, you need to replace the UUID with the right one for that drive.

Save it and reboot.

---

### Post by kallenes on 2009-04-06
how do i edit the fstab? have tried before .. couldnt do it from terminal.
i have the uuid of the SD.
is this something like making the SD persistant?

---

### Post by taurus on 2009-04-06
```
sudo nano -Bw /etc/fstab
```
Once you're done editing, save it and exit with <Ctrl>x and y for the question.

---

### Post by kallenes on 2009-04-06
cant thank you more ... adding it to the fstab worked.
there are many other methods others have posted .. yours was short and simple.
does this make it a permanent member ... like persistant?
thanks again taurus!

---

### Post by taurus on 2009-04-06
Yes, it's permanent unless you remove it from /etc/fstab or your USB is acting up.

---

