---
title: "Nvidia driver and setting don't get along?"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by blualbeddo on 2006-09-08
Hi, this is my first posting. Because I have a typo in my ID, I was waiting for admin to change or delete this ID...but I guess he doesn't want to clean up for other ppl's mistakes...

Anyways, getting into real issue.

I have Nvidia GeForce 6600 graphics card.  I have succeeded on installing its driver to let Dapper utilize it, but it didn't seem like it was giving it much boost.  So I tried to install nvidia-setting, but... when I do, dapper tells me that **nvidia driver will have to be uninstalled in order for nvidia-setting to be installed, and vice versa!!**  What's going on?


And one more thing.  When I use the command 'sudo nvidia-glx-config enable', an error occurs: "Error: your X configuration has been altered." and gives me a command to run md5sum comand.  After running this command the nvidia-glx-config enable command will go through.  However... when I restart x system, it will not start.  I had to edit the file by hand to fix it.  I get that its because the new config file doesn't have correct card port address.  **What I don't get is why enabling glx only works after issuing md5sum command... since I practically made the copied conf file same as the one I had before.**



Well, there you have it. I am very sorry for the long post, but... I guess I am not used to the whole forum thing... yet.


Ok, then this n00b will pc out.

Any help will be greatly appreciated!!

---

### Post by dannyboy79 on 2006-09-08
i read somewhere else that you don't need to 'sudo nvidia-glx-config enable', all you need to do is edit your xorg.conf and change the driver section from "nv" or whatever it was, to "nvidia" and that should do it. As far as the nvidia-setting thing, I am not sure, I didn't have that problem when I followed this, [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper). Good luck to you.

---

### Post by tommcd on 2006-09-10
Nvidia-settings do not need to be installed. I think they are installed along with the driver. If the driver is installed you will see the nvidia splash screen on bootup. To get nvidia settings just type:
nvidia-settings
in terminal and the settings screen should come up.

---

