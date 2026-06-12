---
title: "Orange bar gets stuck"
date: 2008-10-30
forum: General Help
---

### Post by gdogkiller on 2008-10-30
eI am new to the ubuntu stuff. I just started my cd and installed it. so i took the cd out and restarted my cpu. I selected ubuntu. Then it goes to a screen where it says ubuntu and has a orange bar going across the screen. Well it goes back and forth and then it gets stuck. I dont know whats wrong and i need some help badly. so if you could please help me please do. I am using Ubuntu 8.10

Computer Specifications:
Compaq Presario S4200NX Desktop
Windows XP Home Edition
5 Years of age
Connected via router
Using the install without changing windows thing so that when i start up i can choose between ubuntu and windows.

---

### Post by Gannon8 on 2008-10-30
Just so everyone knows, he tried "apci=off" and "start_pcmcia=off". I tried to help him through IM.

---

### Post by Yellow Pasque on 2008-10-30
Sounds like it could be an issue with a corrupted download/burn. Did you verify the MD5 sum of the .iso if you downloaded it directly? Did you burn at a low speed? Did you verify the media using the built-in test on the LiveCD?

---

### Post by Gannon8 on 2008-10-30
Yeah, we downloaded it through DownloadThemAll, and it said it had a correct MD5. We will check the disk with the utility on it.

---

### Post by Gannon8 on 2008-10-30
Yeah, the orange bar gets stuck again, or that is what he is telling me. I think it is a problem with the kernel... Perhaps I can try a diff. distro and see if that works.

---

### Post by Yellow Pasque on 2008-10-30
> **Gannon8 said:**
> Yeah, we downloaded it through DownloadThemAll, and it said it had a correct MD5. We will check the disk with the utility on it.
Good. Assuming the media is ok, go to the GRUB menu, edit the kernel boot line and remove the 'quiet' and 'splash' options so you can see what it is happening when it hangs.

"Orange bar gets stuck" isn't very helpful :P

---

### Post by Gannon8 on 2008-10-30
We are trying to boot from the CD. :)

I asked him to press Ctrl+Alt+F1 (Which I think displays kernel messages and stuff) but he said it didnt do anything :/

This is also a beta cd, downloaded 2 days before release.

---

### Post by Yellow Pasque on 2008-10-30
Ah, if you are trying to boot from the CD, you can still edit your boot options. (IIRC, you press F6).

---

### Post by Gannon8 on 2008-10-30
K, we did that. It looks like it has a problem with the cd drive.
```
[     4.446423]  scsi 1 :0:0:0: CD-ROM            TOSHIBA DVD-ROM SD-M1712 1808 PG
0 ANSI: 5

```

I asked him to take a picture of the screen, so you should get more info in a bit.

---

### Post by gdogkiller on 2008-10-30
```
[  4.038056] 8139cp 0000:02 :0b.0: This (id 10ec :8139 rev 10) is not an 8139C+ compatible chip
[   4.038124] 8139co 0000:02 :0b.0: Try the :8139too" driver instead.
[4.044180] 8139too Fast Ethernet Driver 0.9.28

```

this takes forever but heres some more code im typing though so hopefully soon i will have it all

---

### Post by gdogkiller on 2008-10-30
ok  here is some more

```
[  4.044342] 8139too 0000:02:0b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[4.059279] scsi0 : pata_atiixp
[4.059657] scsi1 : pata_atiixp
```

There is some more

---

### Post by Yellow Pasque on 2008-10-30
Don't type everything on the screen. What is the last line where it hangs?

---

### Post by DougieFresh4U on 2008-10-30
I would in a terminal
```
sudo apt-get -f install
sudo dpkg --configure -a
```
When having had this sort of problem in previous upgrades, I closed the update manager and opened terminal and did the codes I provided. Of course it's not very professional, but it completed my job

---

### Post by gdogkiller on 2008-10-30
the last line is ```
 0 ANSI: 5 
```

---

### Post by Gannon8 on 2008-10-30
> **DougieFresh4U said:**
> I would in a terminal
```
sudo apt-get -f install
sudo dpkg --configure -a
```
When having had this sort of problem in previous upgrades, I closed the update manager and opened terminal and did the codes I provided. Of course it's not very professional, but it completed my job

That has nothing to do with our problem. :confused:
We cannot get into the LiveCD.

To Temüjin:
I posted what he told me was the last line in one of my posts.

---

### Post by Gannon8 on 2008-11-01
We also used a Wubi install on the same computer, with the same problem. I am trying to use an emulator with DSL to see if I can mount the Root.img, but something is not working on his computer.

---

