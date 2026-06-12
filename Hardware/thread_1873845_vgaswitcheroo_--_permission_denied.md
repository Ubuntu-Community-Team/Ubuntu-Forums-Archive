---
title: "vgaswitcheroo -- permission denied"
date: 2011-11-02
forum: Hardware
---

### Post by DerekHe on 2011-11-02
Hi everyone,

I'm using the guide for vgaswitcheroo that allows user access of graphic switching on a Lenovo T400. I have added this into /etc/rc.local (My username is derek):

```

chown derek /sys/kernel/debug/vgaswitcheroo/switch

```

But my access to the "switch" file is still denied like this:
```

derek@Derek-Laptop:~$ ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: Permission denied
derek@Derek-Laptop:~$ sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
-rw-r--r-- 1 derek root 0 Nov  2 13:36 /sys/kernel/debug/vgaswitcheroo/switch

```

It's seen here that the file owner is already set. Anyone here with a solution? Thanks a lot.

---

### Post by lisati on 2011-11-02
First of all, be very careful about doing a chown on system files and folders, it can contribute to system breakage!

You might want to use "sudo" in front of the command that requires admin permissions. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jocko on 2011-11-02
> **DerekHe said:**
> ```

chown [COLOR=Red]**derek**[/COLOR] /sys/kernel/debug/vgaswitcheroo/switch

```But:```
derek@Derek-Laptop:~$ sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
-rw-r--r-- 1 [COLOR=Red]**derek root**[/COLOR] 0 Nov  2 13:36 /sys/kernel/debug/vgaswitcheroo/switch

```
You need to change both user and group permissions, otherwise it will still be inaccessible to you, so this should work:
```

chown [COLOR=Blue]**derek:derek**[/COLOR] /sys/kernel/debug/vgaswitcheroo/switch

```

---

### Post by jocko on 2011-11-02
> **lisati said:**
> First of all, be very careful about doing a chown on system files and folders, it can contribute to system breakage!

You might want to use "sudo" in front of the command that requires admin permissions. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
I agree that it is potentially harmful to to change permissions on system files. It's probably safer to do all the vgaswitcheroo stuff with sudo...

---

### Post by DerekHe on 2011-11-02
Well it's found out that the user doesn't have access to /sys/kernel/debug which is set to 700. Setting it to 755 solves the problem.

---

### Post by Ji Ruo on 2012-02-17
I found the solution to this [here]("http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4") in the answer provided by user42257. I have added the sudo command in front to avoid beginner confusion:

> sudo chmod -R 705 /sys/kernel/debug # this isn't noted on the help.ubuntu-page, yet I had to do this since 11.04
sudo chown -R $YOURUSERNAME:$YOURUSERNAME /sys/kernel/debug/vgaswitcheroo # where $YOURUSERNAME is your user name

---

### Post by _JT on 2012-12-09
> **Ji Ruo said:**
> I found the solution to this [here]("http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4") in the answer provided by user42257. I have added the sudo command in front to avoid beginner confusion:
Is there a way to automate this so I don have to do this every single time I boot? Kind of annoying...

---

