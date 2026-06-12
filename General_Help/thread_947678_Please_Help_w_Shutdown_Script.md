---
title: "Please Help w/ Shutdown Script"
date: 2008-10-14
forum: General Help
---

### Post by rmnstr on 2008-10-14
Hello, I have an IBM R32 Thinkpad Laptop that won't shutdown properly because of my Wireless Card and Network Manager. After doing some searching on Google I found that if I use the command "pccardctl eject" then shutdown it will shutdown fine. I'm not familiar with creating scripts and would appreciate some help setting up a script that will run this command on shutdown. Thanks.

---

### Post by Idefix82 on 2008-10-14
What you need is this very good tutorial on how to manage runlevels:
[http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/]("http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/")

Edit: Just needed to remind myself. You have to put your script into the /etc/init.d folder, name it something like fixnetworks and then execute the command
```
sudo update-rc.d fixnetworks start 02 0 6
```
This will ensure that your script is executed every time you shutdown or reboot after many different modules were killed and after linux-restricted-modules-common is started. Have a look at the tutorial to understand what is going to happen.

---

### Post by gusman21 on 2008-10-21
> **Idefix82 said:**
>  command
```
sudo update-rc.d fixnetworks start 02 0 6
```


your command is missing a period.
```
sudo update-rc.d fixnetworks start 02 0 6 .
```

---

