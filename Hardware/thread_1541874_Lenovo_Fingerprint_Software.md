---
title: "Lenovo Fingerprint Software"
date: 2010-07-29
forum: Hardware
---

### Post by Jaydon H on 2010-07-29
Hey guys,

Upon installing Ubuntu on my Lenovo Thinkpad X200 Tablet, I noticed that there is no other credentials you can authenticate with shown on the login screen. Is there a way to log on with my fingerprint using the Lenovo Fingerprint Software (I have a built-in fingerprint reader)? Thanks for your help.

---

### Post by ronnielsen1 on 2010-07-29
[http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

I haven't had a chance to try it out yet. Let me know if it works

			 		   		 		 		[COLOR=DarkOrange][CENTER]**[SIZE=5]Getting your fingerprint reader to work in Ubuntu[/SIZE]**[/CENTER]
[/COLOR]

---

### Post by Jaydon H on 2010-07-29
It's for Ubuntu Jaunty only, and doesn't work for Lucid. Well, not yet anyway.

---

### Post by ronnielsen1 on 2010-07-30
> It's for Ubuntu Jaunty only, and doesn't work for Lucid. Well, not yet anyway. 	
Just because the site is talking about Jaunty doesn't mean it won't work on Karmic or Lucid. It's when you're trying to install something newer on an older Ubuntu is when you run into library problems.  I just went to synaptic and installed the following files:

fprint-demo libfprint-dev libfprint0 libpam-fprint aes2501-wy
and then started fprint_demo
 and got this window up. (Unfortunately I don't have Ubuntu installed on the laptop yet)

[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-fprintprojectdemo.png[/IMG]

---

### Post by ronnielsen1 on 2010-07-30
OK, just tried it out on my laptop (With fingerprint scanner) and it installed fine but no devices were detected but I haven't given up yet

---

### Post by odd on 2010-08-01
@Jaydon: from what I've read a while ago (on thinkwiki I guess), x200 fingerprint reader hardware is not supported on linux :/ (yet I hope:-)).

---

### Post by Jaydon H on 2010-08-01
Thanks for your help, guys. I guess I'll just have to log in with my 22-character password.

---

