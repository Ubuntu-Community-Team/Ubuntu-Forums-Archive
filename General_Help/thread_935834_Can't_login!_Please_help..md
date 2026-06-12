---
title: "Can't login! Please help."
date: 2008-10-02
forum: General Help
---

### Post by johnlocke2342 on 2008-10-02
Hi.
3 days ago, I tried changing my current GNOME theme in Hardy on my 2-years old PC desktop. I don't know what happened, but it made my computer freeze, and I was obliged to use brute force.
When I rebooted, the system checked my partitions forever. Once finished, I entered my username and password, then my computer displayed an error message "Your session lasted less than 10 seconds..." I went back to the GDM, I choose KDE4, but it displayed the same error message. I tried rebooting, it checked my drive again, but displayed a different error message: "Unable to access to your user folder. If you want, you can choose to login as root..." (I'm not sure of the english translations because I'm using a french-localized Hardy).
I panicked and tried to re-install Ubuntu (my /home directory is on a separated partition). No error messages anymore, but I'm still unable to login in GNOME normally, I have to use the GNOME SAFE environment on login.
I searched this forum, the french forums and Google. There are several cases like mine, but none of the answers works for me.

PLEASE HELP ME !!!

Thanks in advance.

---

### Post by Aero-Z on 2008-10-02
There might be a problem with your settings in your /home directory (folders starting with "."). But that's all I could think of. :(

---

### Post by Ryadt on 2008-10-02
Try this```
sudo /etc/init.d/gdm start
```

---

### Post by johnlocke2342 on 2008-10-02
@Aero-Z: That's what I thought of immediately. But how to fix this?
@Ryadt: It changed nothing!

---

### Post by Ryadt on 2008-10-02
Try reinstalling the ubuntu desktop.
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Aero-Z on 2008-10-02
> **johnlocke2342 said:**
> @Aero-Z: That's what I thought of immediately. But how to fix this?
@Ryadt: It changed nothing!
I don't know :( Maybe someone smarter can tell you where to look.

---

### Post by johnlocke2342 on 2008-10-02
I think you misunderstood me.
I have a GUI, but I can't login unless I use GNOME SAFE mode.

---

### Post by Ms_Angel_D on 2008-10-02
I'm not positive what caused your error or how to fix it but a google search for 

> Your session lasted less than 10 seconds

Returned [THIS POST]("http://ubuntuforums.org/showthread.php?t=97540") as it's top result you may want to try some of the fixes in there.

---

### Post by johnlocke2342 on 2008-10-02
> **MetalHellsAngel said:**
> I'm not positive what caused your error or how to fix it but a google search for 



Returned [THIS POST]("http://ubuntuforums.org/showthread.php?t=97540") as it's top result you may want to try some of the fixes in there.

That's stupid, but I just remembered I had the same problem the 1st time I installed Hardy.
On the French forums, there's a lot of Ubunteros with the same problem, but looks like it's not solved yet.
I reverted to Gutsy, and I'm currently updating to Hardy.

---

