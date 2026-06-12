---
title: "Ubuntu 9.04 resolution Bug"
date: 2009-06-23
forum: Hardware
---

### Post by RussianRoot on 2009-06-23
Hello everyone!
I have a problem with Ubuntu! After installing 9.04, i've installed nvidia-glx. Everything was perfect with resolution (1440x900) after restarting i get always resolution 800x600, but login screeen appiers with good resolution.....
My laptop is Acer Aspire 7520
Please Help!

Thankz!
:)

---

### Post by Arup on 2009-06-23
You should set the resolution settings with nvidia settings and in startup add the entry nvida-settings --load-config-only

---

### Post by RussianRoot on 2009-06-23
> **Arup said:**
> You should set the resolution settings with nvidia settings and in startup add the entry nvida-settings --load-config-only
Could you please say me, how can I add this entry to startup???

Sorry i have been using linux for 4 days...

Thanks!

---

### Post by kingzleshe on 2009-06-23
if you are nvidia so luck to you 
 
you just need download the drive from nvidia.com  
 
after this
 
#sudo /etc/init.d/gdm stop    -- stop the X server   
 

  -- now you are in the tty ,loggin your ubuntu
 
#cd /drive-file
#sudo chmod 777 drive-file-name.sh
#sh drive-file-name.sh
 
select  NO NO ok NO NO, I can;t remember the order. just once OK what Replace your config files.
 
after it done
 
#sudo /etc/init.d/gdm start
 
now everything is ok

---

