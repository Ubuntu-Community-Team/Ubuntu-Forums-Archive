---
title: "Add/Remove Program"
date: 2009-02-26
forum: Hardware
---

### Post by Naz_Farooq on 2009-02-26
Hello Guys, Can you help me out of this problem. I cannot run Add/Remove Program as it shows a problem and when I close the window mentioning problem Add/Remove panel is also closed. I don't know what to do now. I want to migrate from windowsXP to Ubuntu. Please help me out of this problem.

---

### Post by jeremyjjbrown on 2009-02-26
Most commands in Linux that deal with systems changes need to be run as the root user. The error asking if you are root means that you need to start off the command with sudo. See the link below for info on the root user account in Ubuntu linux. You must learn how to use it to use Ubuntu.


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Naz_Farooq on 2009-02-26
> **jeremyjjbrown said:**
> Most commands in Linux that deal with systems changes need to be run as the root user. The error asking if you are root means that you need to start off the command with sudo. See the link below for info on the root user account in Ubuntu linux. You must learn how to use it to use Ubuntu.


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks a lot. But the problem is my Synaptic is also not working and gibing a problem. I will show you that.

---

### Post by Kevbert on 2009-02-26
Please try the following command in Applications-Accessories-Terminal
```
sudo apt-get update
```
With the mouse select the text, so it's highlighted. Press Ctrl-Shift-C to copy it and open a new post and press Ctrl-V to paste it here.

---

### Post by stumbleUpon on 2009-02-26
> **Naz_Farooq said:**
> Hello Guys, Can you help me out of this problem. I cannot run Add/Remove Program as it shows a problem and when I close the window mentioning problem Add/Remove panel is also closed. I don't know what to do now. I want to migrate from windowsXP to Ubuntu. Please help me out of this problem.

A package-manager process seems to be running and so you are not able to use either apt-get or synaptic. See the message you get when you do 'sudo apt-get check' in the second screenshot you have attached.

Kill the process and you should be fine.

find out the process id

```
ps -ef | grep apt-get
```

or if it is synaptic
```

ps -ef | grep synaptic
```

note the process id and then do
```

kill -9 processID
```

---

### Post by Naz_Farooq on 2009-02-26
thanks dear. can you help me for "fence_tool: cman is waiting to start" but it does not start in the booting. I cannot print that page because it is in the beginning.

---

### Post by Naz_Farooq on 2009-02-26
> **Naz_Farooq said:**
> thanks dear. can you help me for "fence_tool: cman is waiting to start" but it does not start in the booting. I cannot print that page because it is in the beginning.

Hello Guys
I have this problem with the start up.
When I boot from ubuntu, it starts reading file needed to boot. Then it says after some time

"fenced [4550]: cman_admin_init error2

dlm_controld [4554]: cman_admin_init error2

gfs_controld [4558]: cman_admin_init error2


fence_tool: waiting for cman to start

fence_tool: waiting for cman to start

ccs [4530]: [ccs] unable to connect to cluster infrastructure after 30 seconds

fence_tool: waiting for cman to start

fence_tool: waiting for cman to start

ccs [4530]: [ccs] unable to connect to cluster infrastructure after 60 seconds"


then it automatically starts saying

"Your CPU does not have extensions to start KVM. Not doing anything."



can anyone help me out of this problem.

---

