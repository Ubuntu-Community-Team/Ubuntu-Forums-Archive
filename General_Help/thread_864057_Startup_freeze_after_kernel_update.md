---
title: "Startup freeze after kernel update"
date: 2008-07-19
forum: General Help
---

### Post by pjalegria on 2008-07-19
Hi 

After last Kernel update (2.6.24.19) startup freezes to start i have to choose last kernel 2.6.24.18

---

### Post by DJPwnage on 2008-07-20
Same thing for me. Idk how to go back tho? can u tell me how? Or do i have to reinstall all over again?

---

### Post by drs305 on 2008-07-20
> **DJPwnage said:**
> Same thing for me. Idk how to go back tho? can u tell me how? Or do i have to reinstall all over again?

Can you boot into a regular session? If so, install startupmanager.  
```
sudo aptitude install startupmanager
```

Then start it (System, Administration, StartUp-Manager) and in the Boot Options section select the older kernel as the Default Operating System.

SUM has lots of settings which allow you to edit and tweak your boot/grub menu safely and easily.

To learn more about StartUp-Manager, read this:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by DJPwnage on 2008-07-20
I can get to the part after i put user and pass.
Then ...nothing just stays in the Tanish color. And i waited like 1 hour. And nothing...so i am guess it froze.

---

### Post by pjalegria on 2008-07-20
I think its a BUG...

---

### Post by DJPwnage on 2008-07-20
... that sucks And it like goes to 1600x1683 idk but really really big every time i try why? even when i was installing it it defaulted to that Res.

---

### Post by DJPwnage on 2008-07-20
Deleted by User

---

### Post by drs305 on 2008-07-20
That is why I asked if you were able to get into your normal system - if you can't proceed to the next paragraph.

Another way to get back to the old kernel is during to hit the ESC key while grub is loading. It will enter an 'edit' mode.

If you have the option to select the previous (working) kernel, do so. 

If you don't see your previous kernel, use the down arrow to select the current one, then hit 'e' to get into the edit mode. Select the line beginning with 'kernel, hit 'e' again and change the kernel number from 19 to 18 (or whatever kernel you were using prior), then hit enter. You can do the same for the line starting with 'initrd' although I don't know if that is necessary.

Once you have made the edits, hit ESC and choose the kernel you just modified.

If you get into your normal system, you can install Startup-Manager, make changes to the boot menu, and then start exploring the reasons kernel 19 didn't work.

If this still doesn't work, we can edit grub's menu.lst from the recovery mode, but the above method will be easier if you can get it to work.

---

### Post by DJPwnage on 2008-07-20
Sorry newb...U mean when the Big logo is on? And the Orange Bar?

umm okay. I just install a fresh vs of Ubuntu 7.10 i386??

I hit Esc and nothing Happens.xD

---

### Post by DJPwnage on 2008-07-20
Fixed Changed Session to GNome andnot Xscript...good or bad?

---

### Post by drs305 on 2008-07-20
> **DJPwnage said:**
> Sorry newb...U mean when the Big logo is on? And the Orange Bar?

umm okay. I just install a fresh vs of Ubuntu 7.10 i386??

I hit Esc and nothing Happens.xD

You would start hitting ESC _before_ you get to the Big Logo. 

If you just did a fresh install, do you realize there is a later version of ubuntu called Hardy. Hardy is version 8.04 and since you are just starting an installation would probably be a better choice than 7.10. It is a LTS (Long Term Support) version and has upgrades that make it worthwhile. 

I would recommend you download the Hardy iso and install that if you are having problems with a fresh install of Gutsy.

---

### Post by DJPwnage on 2008-07-20
i got it to work. But i cant do the thing u told me to 
sudo aptitude install startupmanager
it says i cant. Something about not being a Superuser?

---

### Post by DJPwnage on 2008-07-20
> **DJPwnage said:**
> i got it to work. But i cant do the thing u told me to 
sudo aptitude install startupmanager
it says i cant. Something about not being a Superuser?
yes its saying i am not a superuser and cant install that./

how do i make me a SuperUser?

---

### Post by drs305 on 2008-07-20
> **DJPwnage said:**
> yes its saying i am not a superuser and cant install that./

Are you the only user of the computer? Only root and the first user have administrative (sudo) power by default. If you type 'groups' at the command line you will see an entry 'admin' if you can use 'sudo' to modify system files such as menu.lst

If you aren't listed, you can go back and boot to the recovery mode and run the following command to get administrator privileges:
```
adduser ***yourusername*** admin
```

Reboot and you should now be able to use sudo commands.

I'll be away for awhile but others should be able to help you if you have more questions.

---

### Post by DJPwnage on 2008-07-20
> **drs305 said:**
> Are you the only user of the computer? Only root and the first user have administrative (sudo) power by default. If you type 'groups' at the command line you will see an entry 'admin' if you can use 'sudo' to modify system files such as menu.lst

If you aren't listed, you can go back and boot to the recovery mode and run the following command to get administrator privileges:
```
adduser ***yourusername*** admin
```

Reboot and you should now be able to use sudo commands.

I'll be away for awhile but others should be able to help you if you have more questions.
got the hardy vz. now i am brunning and will install then Update.

---

