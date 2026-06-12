---
title: "ubuntu can't support a higher resolution that my laptop can"
date: 2010-04-14
forum: Hardware
---

### Post by mjsilverstri on 2010-04-14
Hi,

I have a HP laptop which can support 1600x900. But after I install ubuntu 9.10 on it, it can only support up to 1280x700.  My laptop has a Nvidia graphics card. And i am using GNOME as my desktop environment.

Can you please tell me how can I configure ubuntu 9.10 to have 1600x900?

Thank you.

---

### Post by tgm4883 on 2010-04-14
Have you installed the proprietary driver for your video card?

---

### Post by mjsilverstri on 2010-04-14
I went to [http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us). But I am not sure which one to use.  My graphic card is '1GB Nvidia GeForce GT 320M'. But that site does not have one which matches it. So which one should I use?

Thank you.

---

### Post by coffeecat on 2010-04-14
Have a look in System > Administration > Hardware Drivers. Is that prompting you to enable a proprietary driver? That's much easier than downloading and installing from the nvidia site.

---

### Post by mjsilverstri on 2010-04-14
I have tried that. But it comes back nothing.

---

### Post by coffeecat on 2010-04-15
> **mjsilverstri said:**
> I have tried that. But it comes back nothing.

Make sure you are connected to the internet and have updated the package metadata with Update Manager > 'Check', or Synaptic > 'Reload', or 'sudo apt-get update' from a terminal.

---

