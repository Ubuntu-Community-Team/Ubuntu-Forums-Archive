---
title: "rendering = 'none', desktop effects don't work, help please"
date: 2008-06-11
forum: Hardware
---

### Post by cjdawson73 on 2008-06-11
this doesn't look right

Gathering information about your system...

Distribution: Ubuntu 8.04
Desktop environment: GNOME
Graphics chip: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
Driver in use: intel
Rendering method: None

Checking if it's possible to run Compiz on your system... [SKIP]

Checking for hardware/setup problems... [SKIP]

At least one check had to be skipped:
Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by cjdawson73 on 2008-06-11
bump

---

### Post by prshah on 2008-06-12
> **cjdawson73 said:**
> 
Graphics chip: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
Driver in use: intel
Rendering method: None


Can you post your "/var/log/Xorg.0.log" file?

Maybe you should check if you have any conflicting graphics drivers installed (Eg nVidia, ATI), and remove them.

---

### Post by cjdawson73 on 2008-06-13
hmmmm.

chris@dell-desktop:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied

---

### Post by argail1980 on 2008-06-13
argh.. you should use an editor or less, you're trying to execute the logfile
```
less /var/log/Xorg.0.log
```

---

### Post by prshah on 2008-06-13
> **cjdawson73 said:**
> hmmmm.

chris@dell-desktop:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied

When you compose a reply, in the reply window, look for a paper clip icon. Click on that. Then choose browse, and locate the Xorg.0.log file in /var/log/ directory. Select it, then click Open/OK/Select. The click the Upload files button. Then wait a few seconds for the upload to complete. Then close the window and complete the reply, and choose "Submit Reply". That will attach the file mentioned above to your reply.

---

### Post by cjdawson73 on 2008-06-13
Thanks for the help, although when I followed directions I got this after selecting 'upload':

'Upload Errors
Xorg.0.log:
Invalid File '

---

### Post by cjdawson73 on 2008-06-13
how about this

---

### Post by prshah on 2008-06-14
> **cjdawson73 said:**
> how about this

From the log file:> ```

(II) intel(0): direct rendering: Disabled
...
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

You're using Intel, but it's trying to load the nvidia driver. You need to uninstall the nvidia driver. Once you do that, maybe Direct Rendering may get enabled automatically, otherwise we may need to work more on that.

---

### Post by cjdawson73 on 2008-06-14
thanks. is this better?

---

### Post by prshah on 2008-06-14
> **cjdawson73 said:**
> thanks. is this better?

Much. Direct rendering is enabled. AIGLX (renderer) is active.  Try enabling desktop effects the way you did in your first post. It should work. Post back if you get any fresh errors.

---

