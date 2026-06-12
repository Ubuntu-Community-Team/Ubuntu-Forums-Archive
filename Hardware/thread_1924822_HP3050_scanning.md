---
title: "HP3050 scanning"
date: 2012-02-13
forum: Hardware
---

### Post by blackhill on 2012-02-13
I have attached a HP3050a all-in-one printer to my Ubuntu 10.10 system
I installed the HPLIP software recommended by HP for this combination and it prints correctly.
It also copies correctly when activated by the Copy button on the printer interface.
The instructions state that it should be possible to initiate scanning merely by pressing the Scan button on this interface.
However, it will not respond to the Scan button yet it will scan correctly if the scan is initiated with either Simple Scan or Xsane.
Does anyone know a way to resolve this and activate the Scan button?
Thanks.

---

### Post by Acknud on 2012-02-13
I am trying to get a 3050 to be recognized by my 11.10 system.  It will print but I cannot get the scanner recognized.  Did you have to do any tweaking?

---

### Post by blackhill on 2012-02-14
[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)
  
I found that strict compliance with the above download instructions for the appropriate  version of HPLIP for my system allowed me to print and copy as expected.

As stated in my original post, the scan button will not work for me but scanning can be initiated from my downloaded version of Xsane .

If you manage to get the scan button working, I would be grateful to know how.

---

### Post by Another Monkey on 2012-03-26
You are not the only one trying to find out the answer to this question.  I just [posted here]("ubuntuforums.org/showthread.php?t=1926727").

The HP 3050 does not support scan to PC, this is (confusingly) explained in HP documentation.  "No" means "No", "Yes" means "No" and "DS" means "Yes".

---

