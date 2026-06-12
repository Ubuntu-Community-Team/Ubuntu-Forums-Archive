---
title: "can't start compiz"
date: 2008-08-11
forum: General Help
---

### Post by colobix on 2008-08-11
I can't start compiz. I got this code:

Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity

What does it mean and what do I do to fix this issue?


Please help - thanks.

---

### Post by ajgreeny on 2008-08-11
Can you give us more info about your graphics card and the driver it is using.  It is obviously an ati card and appears to be using the open source ati/radeon driver, but which card is it?

---

### Post by colobix on 2008-08-11
I'm using a blacklisted ati card.
I used the compiz-checker script to open the blacklist door.

I tried start it again and got another error:

Here's the full script:
chris@chris-laptop:~$ compiz
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by UbuntuNerd on 2008-08-11
look here [http://ubuntuforums.org/archive/index.php/t-596927.html]("http://ubuntuforums.org/archive/index.php/t-596927.html")

---

### Post by colobix on 2008-08-11
Thanks but this is scary. I don't even know which driver to add and my card name. All I want is the compiz thing to work.
I wish the ubuntu could turn off the blacklist thing in the next version of compiz. the blacklist is nothing but trouble anyway. Insted there should be a simple warning message if your card is risky to use.

---

### Post by colobix on 2008-08-11
But thanks alot. It works fine now.
Finally:):):):):):)

---

