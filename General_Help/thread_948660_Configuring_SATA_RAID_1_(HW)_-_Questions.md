---
title: "Configuring SATA RAID 1 (HW) - Questions"
date: 2008-10-15
forum: General Help
---

### Post by ScottMartin on 2008-10-15
I am in the process of setting up a server using a 3ware SATA RAID controller and I would like to get some thoughts on the setup.

Having setup many Ubuntu boxes, this will be my first RAID server.

Are there any tips/tutorials that anyone could recommend?

My planned setup will be:

Dual Core PC / 4G RAM
1 3Ware 9650-4LPML
1 80G for OS
2 500G RAID 1 for data
1 USB drive for backup 

This will be for a Web Server.

Several immediate questions:

1) Anything wrong w/ this configuration? I gathered this would be the best setup based on several articles I have read in this forum.

2) On setup, will the installer auto-recognize the RAID drive configuration since I am using a controller. Any extra steps required?

3) For development, I have been using LAMPP. For production, I take it that I need to install the "full" versions of each product included in LAMPP for security reasons? or will LAMPP work after modifications? (sure makes things easier to install)

4) If LAMPP is possible the install using the /opt dir for the installs. I do not recall being offered an alternate DIR for install. Since I have my OS on the 80G, would installing the "full" versions allow me to place the web server on the RAID drives and default to the OS drive, correct? Or would I simply re-direct HTDocs to the RAID?

5) Is there any easy way to redirect the /home dir to the RAD drives during install, or does this have to be done after?

6) Is a headless server the best option? I have always used the desktop using x-server, but I am very comfortable w/ the command line.

7) Any gotchas?

Any comments appreciated! TIA

Regards,
Scott.

---

### Post by cariboo on 2008-10-15
> 1) Anything wrong w/ this configuration? I gathered this would be the best setup based on several articles I have read in this forum.

No there is nothing wrong with your setup, that is exactly the way I set up my server, except for the raid card, I used the builtin raid on my motherboard.

> 2) On setup, will the installer auto-recognize the RAID drive configuration since I am using a controller. Any extra steps required?

You will have to create the partitions on your two 500Gb disks first, before setting up the array.

> 3) For development, I have been using LAMPP. For production, I take it that I need to install the "full" versions of each product included in LAMPP for security reasons? or will LAMPP work after modifications? (sure makes things easier to install)


I personally prefer lamp, but it will be installed on your 80Gb drive so it won't make any difference, If you are doing a new installation, of course you should install the full package.

> 4) If LAMPP is possible the install using the /opt dir for the installs. I do not recall being offered an alternate DIR for install. Since I have my OS on the 80G, would installing the "full" versions allow me to place the web server on the RAID drives and default to the OS drive, correct? Or would I simply re-direct HTDocs to the RAID?


I'm not sure where lampp stores the html docs, I assume that it stores them in /opt/var/www, you can create a symlink to a directory on your raid array, or you could change the document route in /etc/apache2/sites-enabled.

> 5) Is there any easy way to redirect the /home dir to the RAD drives during install, or does this have to be done after?


Again while you are partioning your 500Gb drives you an create a /home partiton.

> 6) Is a headless server the best option? I have always used the desktop using x-server, but I am very comfortable w/ the command line.


Again that is up to you, if you feel more comfortable using a gui then install the gui. If the server is going to be a live server, you would probably be better off without the overhead of a gui.

> 7) Any gotchas?

Something will always come up that you haven't run into before if you try to setup services that have never used before. If you run into problems, with anything be sure to go here:

[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

to ask your questions as ther are some pretty smart people that only answer questions in that forum.

Jim

---

