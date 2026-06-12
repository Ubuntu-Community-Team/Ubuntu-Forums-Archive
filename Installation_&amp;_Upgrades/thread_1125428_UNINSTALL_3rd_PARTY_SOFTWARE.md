---
title: "UNINSTALL 3rd PARTY SOFTWARE"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by yildiz.a on 2009-04-14
Do you know how can be a software uninstalled from the system? I use 8.10 

and tried to installed a program. Is there any uninstaller program like on 

Windows apart from Synaptic Packet Manager and Add/Remove Applications? 

Thanks...

---

### Post by fballem on 2009-04-14
> **yildiz.a said:**
> Do you know how can be a software uninstalled from the system? I use 8.10 

and tried to installed a program. Is there any uninstaller program like on 

Windows apart from Synaptic Packet Manager and Add/Remove Applications? 

Thanks...

Could you please be a little more specific? What is the program that you want to remove and how did you install it in the first place. Also, could you please tell us whether you are using the 32-bit or 64-bit version of ubuntu 8.10?

Thanks,

---

### Post by wpshooter on 2009-04-14
Look in the directory wherein the program install was performed from or to and see if there is a text file included which instructs how to uninstall.

---

### Post by yildiz.a on 2009-04-14
I use 32-bit version and installed Xilinx ISE 10.1 but it failed. Another question is: 

Because of failing, is it possible that program abort and delete all files from the 

Filesystem and no need to uninstall?

---

### Post by drs305 on 2009-04-14
> **yildiz.a said:**
> I use 32-bit version and installed Xilinx ISE 10.1 but it failed. Another question is: 

Because of failing, is it possible that program abort and delete all files from the 

Filesystem and no need to uninstall?

Failed during the installation or afterward? If it installed and failed later there is little chance that the program uninstalled itself.

As mentioned previously, try to find the application folder which was created during installation. The README or INSTALL file may give you instructions. If you can find the folder, you can also look within it for an uninstall file or folder with "postinst" in the name.

---

### Post by Tibuda on 2009-04-14
It depends on the software.

If you installed it from source with "./configure && make && sudo make install", you probably can uninstall it running "sudo make uninstall" from the source code directory.

---

### Post by yildiz.a on 2009-04-14
Ok, thank you very much, I will try your suggestions.

---

### Post by babygenius55 on 2009-08-02
Thank you very much. i looked for a while on the forums...had to use google to find this.  Great knowledge.

---

