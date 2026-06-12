---
title: "Nvidia GeForce 8200 -onboard video problem."
date: 2008-09-22
forum: Hardware
---

### Post by fewjr on 2008-09-22
Hello All,
     I have finally gotten my new computer installed with 8.04 Hardy Heron. I am trying to get video to work right. Actually I have gotten it to work to some extent. The video is on board...GeForce 8200, on a GIGABYTE GA-M78SM-S2H. I had to install EnvyNG to get Nvidia drivers that worked. The Restricted driver went to black screen when enabled. With the one Envy installed I can run a better resolution, but if I enable desktop effects something is not right in Firefox. It breaks webpages. I mean lines of text double up and stack on top of one another and soforth. If I go back to no effects...well I say effects. If you go to preferences>appearance then to the Visual Effects tab, if I choose Normal or Extra I get the artifacts in webpages. I'm not sure what else it would mess up. I haven't done much else. I'm still in the process of setting this box up. So I end up setting it back to None. I did go to Synaptic and install CompizFusion, but I only see Appearance under Preferences. I think I need to install some plugins to see Preferences>Advanced desktop settings or whatever it is. Because I don't have any options for adding the cube or anything. So I am wondering if using the onboard video is the same as using an add-in card. I don't know how much memory Geforce 8200 on the motherboard chipset has as apposed to a Geforce 8200 pciexpress card. Can anyone give me some help here? I do have a Geforce 7600GT sitting here I could try, but I thought the onboard would be more advanced.

---

### Post by knix on 2008-09-22
I'm not sure why it does that, but I seem to recall a similar problem. What driver version do you have?

---

### Post by fewjr on 2008-09-22
tahnks for quick reply. I ran "sudo gedit /etc/X11/xorg.conf" and the driver listed is "nvidia" thats it...I do not see a version#.

---

### Post by fewjr on 2008-09-22
I did a search how to find version. code: gksu nvidia-settings = version 173.14.12

---

