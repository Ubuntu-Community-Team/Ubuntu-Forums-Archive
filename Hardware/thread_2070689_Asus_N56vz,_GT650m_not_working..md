---
title: "Asus N56vz, GT650m not working."
date: 2012-10-13
forum: Hardware
---

### Post by ne0phyte on 2012-10-13
Hello!

It seems like ubuntu can not recognize my GPU. -> Details -> Graphics: Unknown.

The system it self eats battery, with poor performance in games etc. 

What do I need to do?

Regards

---

### Post by 2F4U on 2012-10-13
What are your hardware specs? Did you try running the additional drivers utility?

---

### Post by ne0phyte on 2012-10-13
> **2F4U said:**
> What are your hardware specs? Did you try running the additional drivers utility?

These are my hardware specs.
[http://www.asus.com/Notebooks/Multimedia_Entertainment/N56VZ/#specifications](http://www.asus.com/Notebooks/Multimedia_Entertainment/N56VZ/#specifications)

Yes. When running the additional drivers utility it won't find any results.

---

### Post by ddmitriy on 2013-03-25
You need to install Bumblebee and related packages for your NVidia graphics to work. Do NOT attempt to install a package from NVidia site, because those are made for single graphics solutions, which is not the case here.
It's easily achievable from terminal using following commands:
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia nvidia-current

After those, you need to reboot.
To run graphics heavy applications, you must use the following command:

optirun [options] <application> [application-parameters]
or else onboard Intel graphics will be used instead of NVidia one.

To access NVidia chip settings, use the following command:
optirun nvidia-settings -c :8

---

