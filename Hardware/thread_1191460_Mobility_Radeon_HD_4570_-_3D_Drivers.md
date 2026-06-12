---
title: "Mobility Radeon HD 4570 - 3D Drivers?"
date: 2009-06-19
forum: Hardware
---

### Post by speaker219 on 2009-06-19
Are there any drivers for the Mobility Radeon HD 4570 (Dell Studio 1555 laptop) that provide 3d acceleration with ubuntu? 

Googled around and wasn't able to find any for this card.

---

### Post by Yellow Pasque on 2009-06-19
The open-source ati drivers currently don't have 3D hardware acceleration. However, Ubuntu should offer to install the appropriate proprietary driver if you have the 'Restricted' repository enabled in System -> Administration -> Software Sources

You can always install the latest driver from ATI's site manually if you can't figure out how to install the version provided by Ubuntu: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by avilella on 2009-06-20
Can you run this command on a terminal?

lspci | grep VGA

If you see two lines then you have a hybrid graphics card.

---

### Post by speaker219 on 2009-06-20
> **Temüjin said:**
> The open-source ati drivers currently don't have 3D hardware acceleration. However, Ubuntu should offer to install the appropriate proprietary driver if you have the 'Restricted' repository enabled in System -> Administration -> Software Sources

You can always install the latest driver from ATI's site manually if you can't figure out how to install the version provided by Ubuntu: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

I installed the latest drivers manually from ATi's site, and, upon reboot, was greeted with video "noise" -- looked like static on an old TV set.

---

### Post by TOfregato on 2009-09-01
> **speaker219 said:**
> I installed the latest drivers manually from ATi's site, and, upon reboot, was greeted with video "noise" -- looked like static on an old TV set.

Same here...And i've spent the last 4 hours looking for a solution about "ati driver", "ubuntu" and "hd 4570". Any chance to get 3D acceleration on this video card?

---

