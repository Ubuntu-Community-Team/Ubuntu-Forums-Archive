---
title: "[SOLVED] F-Spot &amp;quot;Sending of message failed...&amp;quot;"
date: 2008-11-20
forum: General Help
---

### Post by ricardisimo on 2008-11-20
Here's what I get when I try sending photos by email via F-Spot (Thunderbird is the default mail app.):
```
Sending of message failed.
Unable to open the temporary file /tmp/tmpblahblahblah.jpg. Check your 'Temporary Directory' setting.
```
As per info I found in a bug report, I edited .gconf/apps/f-spot/export/email to have a much longer timeout before deleting the temp files. No dice. Same issue.

I'd greatly appreciate any help. Thanks in advance.

---

### Post by ohzopants on 2008-11-20
Have you checked that the file is being successfully copied to /tmp before it attempts to send it? My guess is that it's a permission issue with /tmp.

Try using /home/yourusername/tmp or some other directory that you have full r/w permissions to.

---

### Post by ricardisimo on 2008-11-20
Can't I just chown and chmod my Home folder and everything in it?

---

### Post by ohzopants on 2008-11-20
You shouldn't have to do that.  You should already have full permissions in your home folder.

From that error it looks like F-Spot is using /tmp.  On my system /tmp is owned by root, so F-Spot may not be able to place the temporary file there.

---

### Post by ricardisimo on 2008-11-20
The only problem with that is that I have been able to send one photo at a time, original size, most of the time. I would have to be quick about it, though, which led me to the previously mentioned bug thread regarding deletion time. So, if I can do it sometimes with one photo, why can't I do it ever with several?

---

### Post by cariboo on 2008-11-20
Does your ISP have a size limit for email?

Jim

---

### Post by ricardisimo on 2008-11-20
Not that I know of, at least I've never gotten there. Besides, it's not getting to the sending part; just spellcheck and fail.

---

### Post by ricardisimo on 2008-11-21
> **ohzopants said:**
> Have you checked that the file is being successfully copied to /tmp before it attempts to send it? My guess is that it's a permission issue with /tmp.

Try using /home/yourusername/tmp or some other directory that you have full r/w permissions to.

What's the easiest way to test this out? Maybe just split the screen with f-spot on one side and nautilus on the other opened to /tmp?

---

### Post by redpotty on 2008-11-27
ricardisimo,
I had the same problem on 64-bit Intrepid using latest f-spot and thunderbird (accessing gmail with POP). I could send an email with attached image as long as I attached the full-size original.  If I tried to send a resized image I got the same error message: check temporary directory settings, etc...

I found this [post]("http://ubuntuforums.org/showthread.php?t=501990") that solved the problem for me.  Not sure if it's the same post you checked.

1. I changed the gconf key /apps/f-spot/export/email/delete_timeout_seconds from 30 to 2400.

2. I also changed the gconf key /Desktop/Gnome/url-handlers/mailto from command field: thunderbird %s to mozilla-thunderbird %s.

3. In thunderbird I changed the account settings for the Draft and Sent items folders to use the folders in my gmail acount rather than the local folders.

I rebooted and tried again. No luck.  I changed the command field in 2. above back to thunderbird %s and after rebooting I could email resized images.

Hope it helps - worked for me

ubuntu, f-spot, thunderbird, email, resized, images, attatchments, temporary, directory, error

---

### Post by ricardisimo on 2008-11-28
2400 seconds? Ouch! I tried 180 or some such. Cool, though... I'll give it a shot. Thanks!

---

### Post by ricardisimo on 2008-12-02
Still not working, however I have discovered that it is specifically a Thunderbird problem. I've set Evolution as my default email app, and now I can send all of the photos I want. It's not ideal, since Evolution has a whole set of frustrations that accompany it, but for sending photos, who cares?

I imagine that Gnome and Mozilla are not playing well together on this issue.

---

### Post by Odemia on 2009-03-27
Was having a similar problem and found out that Thunderbird cannot send attachments with certain characters in their names.  The english character set seems to be fine though.

[url]http://forums.mozillazine.org/viewtopic.php?t=611282&sid=6112f0baabb002d74dc87d303f093606[\url]

I don't see anywhere to rename files in F-Spot, but hopefully the restriction on filenames is fixed in Thunderbird soon.

---

