---
title: "usplash problems"
date: 2008-07-17
forum: General Help
---

### Post by jnw222 on 2008-07-17
i love usplash (the graphical boot screen)
but when i boot from hd it just launches the the moving bar screen but then drops to a cli-like screen and it continues booting
 
similar thing for shutdown it goes to cli-screen and shuts down

how do i repair this

---

### Post by damis648 on 2008-07-17
I had this problem... it has to do with the timeout for a particular event. I never did solve it though... I had to reinstall for another reason.

---

### Post by jnw222 on 2008-07-17
i will try reinstalling usplash

---

### Post by jnw222 on 2008-07-18
didnt work

---

### Post by drs305 on 2008-07-18
Some users have lost their usplash due to a UUID change of the swap file. Use the following to check:
```

sudo blkid -c /dev/null	| grep swap
cat /etc/initramfs-tools/conf.d/resume

```
(Updated to include omitted step identified by coffeecat) 
If they are different you must update the UUID identifier:
```
gksu gedit /etc/initramfs-tools/conf.d/resume
```

```
sudo update-initramfs -u
```

To tweak usplash settings:

```
sudo aptitude install startupmanager
```

System, Administration, StartUp-Manager, Boot Options and also Appearance.

---

### Post by Spaceman9 on 2008-07-18
The easy way to deal with usplash is to install StartUp-Manager from Synaptic. StartUp-Manager can set up everything from which kernel you boot up with to usplash and even a password for grub. 

After install click System>Adminastration>StartUp-Manager and type in your login password. Click the menu header "Appearance" and at the bottom is Usplash themes. Set Usplash theme to usplash-theme-ubuntu if you want the default Ubuntu theme.

---

### Post by coffeecat on 2008-07-18
> **drs305 said:**
> Some users have lost their usplash due to a UUID change of the swap file. Use the following to check:
```

sudo blkid -c /dev/null    | grep swap
cat /etc/initramfs-tools/conf.d/resume

```If they are different:
```
sudo update-initramfs -u
```

I agree with you up to the 'if they are different' point. But if they are different you have to edit /etc/initramfs-tools/conf.d/resume so that they are the same and only then run sudo update-initramfs -u.

---

### Post by drs305 on 2008-07-18
> **coffeecat said:**
> I agree with you up to the 'if they are different' point. But if they are different you have to edit /etc/initramfs-tools/conf.d/resume so that they are the same and only then run sudo update-initramfs -u.

You are correct. I forgot to post a step. I give you credit. I will update the entry so if someone doesn't read the entire thread they won't be wasting their time.

---

### Post by coffeecat on 2008-07-18
> **drs305 said:**
> You are correct.

No problem. :) I multiboot and I've had to do this so often when installers reformat the swap partition that the method is seared indelibly on my heart. :(

---

### Post by Jose Catre-Vandis on 2009-12-18
This didn't work for me on my multi boot system.

Using grub2 on Jaunty , with W7 and XP and Karmic.

I did have to change the UUID but still usplash dropped to CLI after initial excitement!

---

