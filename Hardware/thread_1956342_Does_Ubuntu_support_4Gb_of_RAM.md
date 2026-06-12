---
title: "Does Ubuntu support 4Gb of RAM?"
date: 2012-04-10
forum: Hardware
---

### Post by wbosher on 2012-04-10
I currently have 2G of RAM and am thinking about putting in another 2. Under Windows XP this isn't really worth it as it only sees a max of 3. Will I see any benefit in the latest version of Ubuntu? Or even the current 11.10? Will it see all 4G?
 
My PC is pretty old now, has an ASUS P5KPL AM/PS board with a 2G Intel dual core processor.
 
Cheers in advance.  :)

---

### Post by PapaGary on 2012-04-10
> **wbosher said:**
> I currently have 2G of RAM and am thinking about putting in another 2. Under Windows XP this isn't really worth it as it only sees a max of 3. Will I see any benefit in the latest version of Ubuntu? Or even the current 11.10? Will it see all 4G?
 
My PC is pretty old now, has an ASUS P5KPL AM/PS board with a 2G Intel dual core processor.
 
Cheers in advance.  :)
Only if you have a 64 bit processor.

---

### Post by wbosher on 2012-04-10
I only have a 32 bit :( Is 2G about all I can use?

---

### Post by PhantomTurtle on 2012-04-10
You can always use pae(lets you use up to 64GB RAM) which is automatically installed if your processor supports it by Ubuntu 10.04 or later.

---

### Post by wbosher on 2012-04-10
Ho can I tell if it's installed/supported? Sorry if this seems like a silly question - noob here.

---

### Post by PhantomTurtle on 2012-04-10
Look here: [https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

---

### Post by 3Miro on 2012-04-10
The regular 32-bit kernel should see little over 3GB of memory (if you have 4GB to begin with). Depending on your motherboard and video card, you may be able to see almost all of the 4GB.

PAE kernel will see all 4GB, although it should be a bit slower (not much). PAE is installed by default if the system detects 4GB of RAM, if you are upgrading a current installation, you should install PAE manually.

Is this your motherboard?
[http://www.asus.com/Motherboards/Intel_Socket_775/P5KPLAMPS/](http://www.asus.com/Motherboards/Intel_Socket_775/P5KPLAMPS/)

If so, then you can just install 64-bit Ubuntu, there is no point of dealing with PAE. Core 2 Duo and higher CPUs have great 64-bit support. If I were you, I would just get the extra RAM and wait for Ubuntu 12.04 to make a clean 64-bit install.

---

### Post by wbosher on 2012-04-10
Yep, that's my board. I might go ahead and upgrade the RAM then...after I get spending permission from the wife  ;)

---

### Post by mastablasta on 2012-04-11
yeah if you have 64 bit processor and more ram there is no need to use 32 bit system.
 
64 bit linux (AMD64 image) allows up to 256Gb RAM and huge file sizes.:
 
**Intel x86**

[LIST]
[*]Maximum CPUs: 32 (including logical CPUs)
[*]Maximum memory: 64GB
[*]Maximum filesize: 8TB
[*]Maximum filesystem size (ext3): 16TB
[*]Maximum per-process virtual address space: 4GB
[/LIST]**AMD 64/EM64T (CentOS 5.x/RHEL 5.x Linux specific info)**

[LIST]
[*]Maximum CPUs: 256
[*]Maximum memory: 256GB
[*]Maximum filesize: 8TB
[*]Maximum [filesystem size]("http://www.cyberciti.biz/howto/question/static/maximum-partition-size.php") (ext3): 16TB
[*]Maximum per-process virtual address space: N/A
[/LIST]Lets not even get started with clusters....
 
but ofcoruse it all depends on motherbaord as well.
 
 
additonally a PAE kernel is also available for windowsXP. it will recognise 4GB ram but 1 Gb will be used for system and programmes will be given 3 GB ram only.

---

### Post by stchman on 2012-04-11
4GB of RAM is the maximum amount a 32 bit OS can use.

To use more than 4GB, you will need to upgrade to a 64 bit OS.

---

### Post by wbosher on 2012-04-11
Thanks guys for all your help. I think 4G of RAM will be more than enough for what I need. :p

---

