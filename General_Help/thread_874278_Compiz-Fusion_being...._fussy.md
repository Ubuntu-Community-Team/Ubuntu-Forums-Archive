---
title: "Compiz-Fusion being.... fussy?"
date: 2008-07-29
forum: General Help
---

### Post by Doug.Henry on 2008-07-29
So last night I took a run at it and installed ubuntu for real, on a computer that is going to be used by some of the most incompetent people i've ever met, computer wise. I'm talking like 20 internet explorer toolbars, people.


I installed compiz-fusion and got everything to work fine in my adminstratior(home) account and I was quite proud of myself, I go to make other user accounts(these people are very private)


now on any other user account other then (home), it says that the enhancements are disabled, and I can't turn them on, any suggestions as to why it works for one, but not all? I'm not a noob entirely but i'm pretty green.

The faq doesnt say anything I don't think.



Thanks =)

---

### Post by klange on 2008-07-29
Try and run `compiz` in a terminal from one of these accounts and report back.

---

### Post by Doug.Henry on 2008-07-29
From the working account or the nonworking accounts? or both?

---

### Post by steveneddy on 2008-07-29
> **Doug.Henry said:**
> From the working account or the nonworking accounts? or both?

The non-working account.

---

### Post by Doug.Henry on 2008-07-29
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (blur) - Warn: No stencil buffer. Region based blur disabled
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.



from the working account(home)

---

### Post by Doug.Henry on 2008-07-29
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :20.0



and the non-working account, any help?

---

### Post by Sam Lars on 2008-08-24
I know this post is a bit old, but, if you're still having this problem, what video card are you using?

---

### Post by ferrarix on 2008-08-24
> **Sam Lars said:**
> I know this post is a bit old, but, if you're still having this problem, what video card are you using?
If it had to be a VGA problem, it wouldn't work on his home account either though.

---

