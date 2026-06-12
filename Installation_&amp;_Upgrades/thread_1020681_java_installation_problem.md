---
title: "java installation problem"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by h33d sight3d on 2008-12-24
i have downloaded java from the java website and i go and try to install  it and it errors
like this
---------------------------------------------------------------------------
Could not open the file /home/
dave/Desktop/jre-1_5_0_02-linux-amd64.bin.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
---------------------------------------------------------------------------
can someone help me please...:confused:

---

### Post by taurus on 2008-12-24
```
cd ~/Deskop
chmod 755 jre-1_5_0_02-linux-amd64.bin
sudo mv jre-1_5_0_02-linux-amd64.bin /opt
cd /opt
sudo ./jre-1_5_0_02-linux-amd64.bin
```
Unless you just want to unpack/install it in your own $HOME/Desktop.

---

### Post by namdung on 2008-12-24
Use Synaptic Package Manager for hassle free installation of Java.

---

### Post by jamesstansell on 2008-12-25
> **h33d sight3d said:**
> i have downloaded java from the java website and i go and try to install  it and it errors
like this
---------------------------------------------------------------------------
Could not open the file /home/
dave/Desktop/jre-1_5_0_02-linux-amd64.bin.



Good advice from both taurus and namdung, depending on your needs.

I'm wondering - why and how did you download such an old JRE version?

---

