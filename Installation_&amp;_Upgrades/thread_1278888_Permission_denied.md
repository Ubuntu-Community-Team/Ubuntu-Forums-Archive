---
title: "Permission denied"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by Jompa on 2009-09-30
I'm trying to install a program but have problem with not getting permission when I try starting the setup file in the terminal. I get this message:
> jonpeder@jonpeder-laptop:~$ cd /home/jonpeder/Spss_17_Linux/
jonpeder@jonpeder-laptop:~/Spss_17_Linux$ ./setup.bin
bash: ./setup.bin: Permission denied

What can I do to get permission? I have tried to use SUDO, but it doesn't seem to do anything.

---

### Post by Waappu on 2009-09-30
Hi,

Try
```
cd /home/jonpeder/Spss_17_Linux/
sudo chmod a+w setup.bin
sudo ./setup.bin

```

---

### Post by atomizer on 2009-09-30
Is the file executable?


else you have to do ```
sudo chmod +x /path/to/file
```
( +x makes the file executable)
After this command you should be able to execute your file.

---

### Post by Jompa on 2009-09-30
I hadn't made the file executable, but after doing thet it worked, thanks :)

---

