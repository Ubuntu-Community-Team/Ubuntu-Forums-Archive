---
title: "Installing k3b"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by sparks40 on 2005-03-30
I'm having trouble installing k3b via. Synaptic on the new hoary-rc released today. I attempted to use Synaptic's search function which listed two files. I applied the files via Synaptic. However, when I start k3b (in a root terminal) I get the error message that "cdrdao" is missing. I have tried to search for cdrdao via Synaptic but it is not to be found using the standard repositories. Has anyone solved this problem?

TNX

---

### Post by fackamato on 2005-03-31
->

> root@fackamato:/mnt/hda2/temp # apt-cache search cdrdao
k3b - A sophisticated KDE cd burning application
k3blibs - The KDE cd burning application library - runtime files
arson - KDE frontend for burning CDs
cdrdao - Disk-At-Once (DAO) recording of audio and data CD-Rs/CD-RWs
jack - Rip and encode CDs with one command
k3b-i18n - Internationalized (i18n) files for k3b
k3blibs-dev - The KDE cd burning application library - development files
simplecdrx - SimpleCDR-X is a frontend for CD writing and mastering
vcdtools - Creates Video CD (VCD) filesystem images


---

### Post by sparks40 on 2005-03-31
Thanks for the reply. Does it mean that I will have to apt-get each of the files you mentioned seperately? I'm not sure that I fully understand what has to be done.

---

### Post by fackamato on 2005-03-31
[QUOTE=sparks40]Thanks for the reply. Does it mean that I will have to apt-get each of the files you mentioned seperately? I'm not sure that I fully understand what has to be done.[/QUOTE]

cdrdao has its own package. Install that.

---

### Post by robin on 2005-04-04
Do you mean download the package through Sourceforge.net?
Is there a reason why it is not available through Kynaptic?

---

### Post by fackamato on 2005-04-04
[QUOTE=robin]Do you mean download the package through Sourceforge.net?
Is there a reason why it is not available through Kynaptic?[/QUOTE]

Huh? Just apt-get install it.

---

### Post by robin on 2005-04-04
Allright, if you say so.
I've never done that before so this will be scary.

---

### Post by fackamato on 2005-04-04
[QUOTE=robin]Allright, if you say so.
I've never done that before so this will be scary.[/QUOTE]


You have never apt-get installed something!? You're in Debian, man! (ubuntu)

How were you planning on installing things if not using dpkg, apt-get or synaptic!?

---

### Post by robin on 2005-04-04
That's right I never have.  I'm still learning and figuring things out as I go along.
I've used kynaptic (I'm using Kubuntu), and if I have to use apt-get I'll figure that out too.

---

### Post by penguinwarrior on 2005-04-05
in a console, just type

   sudo apt-get install cdrdao

in kynaptic or synaptic (i've never used kynaptic or even looked at it, but i gather it's like synaptic), just do a search on
   cdrdao
then click on it, click install, then click on apply on the top panel
(sudo apt-get install cdrdao is so easy and clean and fast though  8) )

you have to have the warty universe repository activated
(in synaptic/kynaptic?) click on settings ->repositories -> then click the box beside where it says deb http...etc warty universe. this will activate the universe repository where cdrdao resides.

and welcome to linux and ubuntu... here to help.

---

### Post by ubuntu_newbie on 2005-04-24
I tried installing k3b via synaptic and found the same "error" regarding missing *cdrdao* . Here is how it was solved.

1. Download cdrdao package from ubuntu website 
    [http://packages.ubuntu.com/hoary/otherosfs/cdrdao](http://packages.ubuntu.com/hoary/otherosfs/cdrdao)

2. Navigate to the directory where you downloaded the a/m file to and do :
    glenn@ubuntu$ dpkg -i *.deb

3. Once cdrdao is installed successfully, move back to Synaptic and do a search for k3b.

4. Install and enjoy !

---

