---
title: "CPU and GPU get very hot"
date: 2009-12-02
forum: Hardware
---

### Post by nbpage on 2009-12-02
Hi
I have a Dell M90. Within 20 minutes of idling my CPU is 55c or over and my GPU is 60c or more.

Surfing or any other light activity raise the GPU to over 70. And playing a 3d game will put it at 85+.

In windows the CPU doesn't get over about 45 unless it's working hard and the GPU tops out at about 65.

Any thoughts? 

I used [I8kfanGUI Fan Control Utility]("http://www.diefer.de/i8kfan/index.html") in windows but can't find anything similar for Ubuntu (I have found some downlaod links but there's no file at the other end)

Thanks

---

### Post by nbpage on 2009-12-03
Anyone?

---

### Post by gradinaruvasile on 2009-12-03
In fact there  are i8k utilities in ubuntu. I use them on a Dell D630.
In a terminal:

sudo apt-get install i8kfan i8kutils
sudo modprobe i8k (surely it begins with i8k, may be something more to it, just press tab)

There is a small gui in the i8kutil package that permits seting fan speeds. I dont know the exact name, but its i8kmon or something. Type i8k and press tab. You'll see the available options.
Also i found nvclock helpful ( My paltop has Nvidia Quadro NVS 135M card).

---

### Post by nbpage on 2009-12-03
Hi

And thanks for replying.

I followed you instructions and ended up with a mssg:

 * Not starting. Disabled via /etc/default/i8kmon.
 * Not starting. Disabled via /etc/default/i8kbuttons.

How can I enable it?

Sorry - I am a complete noob to Linux command line stuff.

Thanks

---

### Post by gradinaruvasile on 2009-12-03
You must edit the files that are in the error message:

/etc/default/i8kmon
/etc/default/i8kbuttons

You can do it by (in a terminal) typing: 

sudo gedit /etc/default/i8kmon

and

sudo gedit /etc/default/i8kbuttons

From the i8kbuttons file:
There is 0 (meaning no) - change it to 1:

# Change to one to enable i8kbuttons
[COLOR="Red"]ENABLED=1[/COLOR]

From the i8kmon file - the same as the i8kbuttons:
Change the 0 to 1:

# Change to one enable i8kmon
[COLOR="#ff0000"]ENABLED=1[/COLOR]

Save the files and reboot.

---

### Post by nbpage on 2009-12-03
I did that and verified the 1's were in place after reboot.

But... now what? :-)

I looked in the Applications and System menus and didn't find anything. I looked online for how to run an app from the cmd line but it didn't work.

So - now I'm bugging you again - sorry.

And thanks

---

### Post by 311005901 on 2009-12-03
> **nbpage said:**
> Hi
I have a Dell M90. Within 20 minutes of idling my CPU is 55c or over and my GPU is 60c or more.

Surfing or any other light activity raise the GPU to over 70. And playing a 3d game will put it at 85+.

In windows the CPU doesn't get over about 45 unless it's working hard and the GPU tops out at about 65.

Any thoughts? 

I used [I8kfanGUI Fan Control Utility]("http://www.diefer.de/i8kfan/index.html") in windows but can't find anything similar for Ubuntu (I have found some downlaod links but there's no file at the other end)

Thanks

I've got this problem also. I need something to force the fan to spin faster.

---

