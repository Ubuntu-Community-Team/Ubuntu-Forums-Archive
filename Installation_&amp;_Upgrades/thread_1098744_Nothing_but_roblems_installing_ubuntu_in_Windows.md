---
title: "Nothing but roblems installing ubuntu in Windows"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by Brierley24 on 2009-03-17
I am experiencing nothing but problems in trying to install ubuntu within Windows.

I am now on my twenty third attempt! The furthest I have got is to the "Installing System" "Scanning Files" screen which continously freezes at 15%. I am running XP Pro on a aci laptop. I have tried both the CD that I down-loaded from the ubuntu website and the CD sent through the post. Both are 8.10.

I do like ubuntu but I'm losing patience rapidly. Has anyone any ideas?

Thanks

---

### Post by TenPlus1 on 2009-03-17
Are you using the 32-bit or 64-bit version of Ubuntu ?

If it's the 64-bit version, try switching to 32 and see if it boots from the actual CD 1st before isntalling...

---

### Post by Brierley24 on 2009-03-17
Thanks for the reply. I can boot from the CD which runs the Live CD trial version. I would do a complete install but I'm unsure for the partitioning procedure. (I don't want to lose windows and all my data) I have checked the CD cover and disc, there is no mention of whether it is 32 or 64. How do I find out?

Thanks

---

### Post by TenPlus1 on 2009-03-25
I dunno what the problem could be unless the cd's are somehow faulty...  The wubi (inside windows) install should simple copy the files across and setup ubuntu on first boot...  The fact it's working from the LiveCD means the cd's are ok... hmm... weird!

---

### Post by ago on 2009-03-27
What are your machine specs? You might have too low ram. Also you might want to try wubi 9.04 beta. For errors on the Linux side installation, press ESC at boot after selecting Ubuntu and select verbose/debugging mode. You can press CTRL+ALT+F2 during installation to get a shell. The relevant log is /var/log/syslog

---

