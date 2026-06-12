---
title: "Two PCs and Updates download, How to?"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by saidbakr on 2009-09-07
Hello,

I would like to know does it possible to get updates from local machine that downloaded updates?

I have local area network in my house and I have two PCs which both of them runs Ubuntu. To safe traffic from the Internet, I would like to make one of them downloads updates and the other one get these updates from it without need to use the Internet traffic again. Does this possible to be achieved in Ubuntu?

---

### Post by running_rabbit07 on 2009-09-07
That would be really hard unless both systems have the exact same hardware.

---

### Post by Cheezespread on 2009-09-07
The updates in general downloaded will be available as deb files in **"/var/cache/apt/archives"**. You can copy them to the second PC's **"/var/cache/apt/archives"** directory and use it i believe. Please correct me if i am wrong.

---

### Post by joelgsf on 2009-09-09
The solution given by Cheezespread does work, I can assure that, as I have used it more than once. It is not required that the machines be identical, just that they be running the same version of Ubuntu. I have used this scheme sucssefuly between a Core 2 Quad desktop and a Core 2 Duo notebook without any problem. In my case, both run Jaunty amd64. Obviously you may import, this way, something which will not be used on the other machine and may miss something you need, but, anyway, the download required is reduced significantly.
Happy cloning! :)

---

### Post by itisbasi on 2009-09-09
use aptoncd...I use it to update my standalone machine...it's available in the repos..

---

### Post by running_rabbit07 on 2009-09-09
> **itisbasi said:**
> use aptoncd...I use it to update my standalone machine...it's available in the repos..
APTonCD is good for backing up your updates for a future reinstall, but a waste of disks if the two systems are networked. I use rewritable disks when I use APTonCD, but not for that purpose.

---

### Post by itisbasi on 2009-09-09
> **running_rabbit07 said:**
> but a waste of disks

Not really. Once APTonCD is installed on the machine without internet connection(for which it needs to be burnt on to a CD or use the aptoncd.deb file from /var/cache/apt/archives), I can start APTonCD and update directly from the ISO, not having to burn and waste disks everytime.

---

### Post by speedync on 2009-10-03
I'm pretty new to Ubuntu, and I don't seem to be able to paste the updates into the /archives folder on the standalone machine. Not with the GUI anyway. Can anyone give me some pointers on how to do this? Thanks in advance.

---

### Post by drs305 on 2009-10-03
> **speedync said:**
> I'm pretty new to Ubuntu, and I don't seem to be able to paste the updates into the /archives folder on the standalone machine. Not with the GUI anyway. Can anyone give me some pointers on how to do this? Thanks in advance.

One of the reasons is that the files in these folders are owned by *root*, so you have to have admin privileges to perform the action. Open Nautilus as "root" with this command (Open a terminal via Applications, Accessories, Terminal):
```

gksu nautilus

```
Navigate to the files you want to copy, highlight them, then right click your mouse and select "Copy". Go to the folder where you want to copy them, right click and "Paste" (or highlight the folder and select "Paste into folder").

If your questions concern a Network and how to perform the actions across a Network and not simply between two partitions, let us know.

---

### Post by speedync on 2009-10-03
> **drs305 said:**
> One of the reasons is that the files in these folders are owned by *root*, so you have to have admin privileges to perform the action. Open Nautilus as "root" with this command (Open a terminal via Applications, Accessories, Terminal):
```

gksu nautilus

```
Navigate to the files you want to copy, highlight them, then right click your mouse and select "Copy". Go to the folder where you want to copy them, right click and "Paste" (or highlight the folder and select "Paste into folder").

If your questions concern a Network and how to perform the actions across a Network and not simply between two partitions, let us know.

Thankyou very much for that drs305. I actually downloaded the APTonCD from synaptic, and copied the ISO onto a USB drive instead of burning it onto a CD, and simply plugged it into the other machine. Worked a treat:) I will also try your method. I am having a marvelous time learning a new operating system along with new ways of doing things.
A bit off topic -but any idea of a good thread on how to share files between 2 Ubuntu computers over a network? Once I understand that then I'll be keen to hear how to do it over a network (update that is). 
I can share windows files over the network using samba (from a windows machine to an Ubuntu machine and vice versa) but I have not figured out how to do it between 2 Ubuntu computers. Cheers and thanks for the info:)

---

### Post by drs305 on 2009-10-03
> **speedync said:**
> I can share windows files over the network using samba (from a windows machine to an Ubuntu machine and vice versa) but I have not figured out how to do it between 2 Ubuntu computers. Cheers and thanks for the info:)

I use SSH, which provides a secure connection, but I'm often "accused" of overkill. You can use samba, SSH, or NFS. Here is a thread which discusses some of them:
[http://ubuntuforums.org/showthread.php?p=7988509]("http://ubuntuforums.org/showthread.php?p=7988509")

---

### Post by speedync on 2009-10-03
Thankyou again drs305. The amount of information and support on these forums is amazing. I installed SSH on both computers, set it up as described and again, it works a treat. Simple and it works. Thankyou :)

---

