---
title: "[SOLVED] Canon PIXMA MP830"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by Megaqwerty on 2007-03-04
I am having some trouble getting the Canon PIXMA MP830 to work with Ubuntu. Despite the vast amount of printers that are supported out of the box with Ubuntu, this one doesn't seem to be listed.

I went to [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP830](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP830) and found that gutenprint supports it.

Can someone help me install it? (Preferably in steps)

Thanks,

Megaqwerty

---

### Post by etotehpii on 2007-03-04
I have the same printer and was able to get it to work with CUPS.  However, for whatever reason, the printer configs I set up through CUPS disappeared and I have been unable to print with it despite repeated efforts to configure through CUPS.:( 

Are you printing wirelessly?

---

### Post by Megaqwerty on 2007-03-04
> **etotehpii said:**
> I have the same printer and was able to get it to work with CUPS.  However, for whatever reason, the printer configs I set up through CUPS disappeared and I have been unable to print with it despite repeated efforts to configure through CUPS.:( 

Are you printing wirelessly?

Yes, I am printing wirelessly, and the printer is shared on a Windows box...will it still work through CUPS?
(If so, could you show me an example of how you configured it?)

Thanks.

---

### Post by etotehpii on 2007-03-05
I wish I knew what I did with CUPS to get it printing.

All I know is after trying various combinations of settings I got it working for a few weeks and then it stopped working.  I've periodically tried through CUPS with various settings and have had no luck.

---

### Post by Megaqwerty on 2007-03-06
> **etotehpii said:**
> I wish I knew what I did with CUPS to get it printing.

All I know is after trying various combinations of settings I got it working for a few weeks and then it stopped working.  I've periodically tried through CUPS with various settings and have had no luck.

While your comments don't  help me in my situation, I will lend you some advice. Whenever you do something critical, keep a text document of what you did, so

1) If something goes wrong, you can go back and undo it.
2) You can show others how you accomplished it.
3) You can create a shell script to automate the task should you need to.

Back on topic: Can anyone give me some help?

---

### Post by Megaqwerty on 2007-03-17
*Bump*

---

### Post by etotehpii on 2007-03-29
I finally got some time to play around with it again and I got it working.

```
 sudo apt-get install cupsys*
```

That is the only new thing I've done.

Good Luck.

---

### Post by Megaqwerty on 2007-03-29
Cool! I hadn't gotten around to checking out the supported printers in Feisty Fawn (which I upgraded to a couple days ago) and I have awesome news! The PIXMA MP830 is supported in Feisty! However, the driver is listed under "MULTIPASS MP830" so for me, it works through SMB as well. 

Thanks for your help earlier,

Megaqwerty

---

### Post by kmccutcheon on 2007-05-16
Well, I'm going to jump on this thread so I don't have to start a new one, but I'm having the same issue. I'm using Dapper, and am not anxious of upgrading to Feisty.  Thought I followed the instructions correctly for gutenprint, but I'm not having any luck. Here is a copy of the error log:
E [15/May/2007:16:39:08 -0700] CUPS-Delete-Printer: Unauthorized
E [15/May/2007:16:40:05 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:16:40:18 -0700] PID 22370 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [15/May/2007:16:40:18 -0700] [Job 14] No %%BoundingBox: comment in header!
E [15/May/2007:16:40:39 -0700] cupsdAuthorize: Local authentication certificate not found!
E [15/May/2007:16:40:40 -0700] cupsdAuthorize: Local authentication certificate not found!
E [15/May/2007:16:40:40 -0700] cupsdAuthorize: Local authentication certificate not found!
E [15/May/2007:16:40:40 -0700] cupsdAuthorize: Local authentication certificate not found!
E [15/May/2007:16:45:47 -0700] cupsdAuthorize: Local authentication certificate not found!
E [15/May/2007:16:45:50 -0700] cupsdAuthorize: Local authentication certificate not found!
E [15/May/2007:16:45:50 -0700] CUPS-Delete-Printer: Unauthorized
E [15/May/2007:16:47:51 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:16:49:35 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:06:45 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:07:36 -0700] PID 24562 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [15/May/2007:17:07:36 -0700] [Job 16] No %%BoundingBox: comment in header!
E [15/May/2007:17:07:51 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:08:31 -0700] PID 24686 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [15/May/2007:17:08:31 -0700] [Job 17] No %%BoundingBox: comment in header!
E [15/May/2007:17:10:12 -0700] cupsdAuthorize: Local authentication certificate not found!
E [15/May/2007:17:10:12 -0700] cupsdAuthorize: Local authentication certificate not found!
E [15/May/2007:17:14:02 -0700] cupsdAuthorize: Local authentication certificate not found!
E [15/May/2007:17:18:15 -0700] Purge-Jobs: Unauthorized
E [15/May/2007:17:18:28 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:18:28 -0700] Purge-Jobs: Unauthorized
E [15/May/2007:17:19:27 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:19:30 -0700] CUPS-Delete-Printer: Unauthorized
E [15/May/2007:17:19:33 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:19:33 -0700] CUPS-Delete-Printer: Unauthorized
E [15/May/2007:17:19:50 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:20:16 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:20:27 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:20:27 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:20:37 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:20:37 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:20:46 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:20:46 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:20:55 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:20:55 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:21:07 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:21:07 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:21:25 -0700] CUPS-Delete-Printer: Unauthorized
E [15/May/2007:17:22:19 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:22:30 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:22:30 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:22:39 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:22:39 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:22:43 -0700] cupsdAuthorize: Empty Basic password!
E [15/May/2007:17:22:43 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:22:54 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:22:54 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:23:11 -0700] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/May/2007:17:23:11 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:29:04 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:29:41 -0700] PID 26221 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [15/May/2007:17:29:41 -0700] [Job 18] No %%BoundingBox: comment in header!
E [15/May/2007:17:37:50 -0700] CUPS-Delete-Printer: Unauthorized
E [15/May/2007:17:38:35 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:40:29 -0700] PID 27217 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [15/May/2007:17:40:29 -0700] [Job 19] No %%BoundingBox: comment in header!
E [15/May/2007:17:43:47 -0700] CUPS-Delete-Printer: Unauthorized
E [15/May/2007:17:45:22 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:17:45:36 -0700] PID 28101 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [15/May/2007:17:45:36 -0700] [Job 20] No %%BoundingBox: comment in header!
E [15/May/2007:17:57:18 -0700] CUPS-Delete-Printer: Unauthorized
E [15/May/2007:17:57:26 -0700] cupsdAuthorize: Empty Basic password!
E [15/May/2007:17:57:26 -0700] CUPS-Delete-Printer: Unauthorized
E [15/May/2007:17:58:13 -0700] PID 28854 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [15/May/2007:17:58:51 -0700] PID 28919 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [15/May/2007:18:05:21 -0700] CUPS-Delete-Printer: Unauthorized
E [15/May/2007:18:06:58 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [15/May/2007:18:07:09 -0700] PID 29507 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!

What am I missing? Is this the appropriate forum for this question?

Thanks.

---

