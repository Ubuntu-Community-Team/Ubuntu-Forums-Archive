---
title: "Lotus Notes 8.0.2 on Intrepid Ibex"
date: 2008-11-04
forum: General Help
---

### Post by ew1 on 2008-11-04
Has anyone had any luck successfully installing Lotus Notes 8.0.2 on Ibex.  I did a clean install of 8.10 and then installed LN, everything appears to work except the integrated sametime messaging, it shows all of my contacts but will not let me chat with them, it will not even open the chat window.

I then tried to install 8.0.1 to see if that would fix the problem, but I couldn't even get that to install,

Any suggestions on how to make the chat work in Lotus Notes 8.0.2?

---

### Post by ew1 on 2008-11-06
In case anyone runs into the same problem I had, I disabled the internal web browser inside of Lotus Notes, and told it to use my system default browser which fixed the problem with the integrated sametime client.

---

### Post by Joseph Brown on 2008-11-11
ew1, have you had any other issues with Lotus Notes on Intrepid. Mine has been locking up?

---

### Post by ju2wheels on 2008-11-11
Lotus Notes is Java based in version 8 so I would make sure your system is not using OpenJDK as the default java vm but rather using Sun or IBM's if theres a linux version available.....

Edit:

I would also double check the permissions of the settings folder it creates in your home directory, as I recall for Lotus Symphony it caused problems because the permissions were set to root instead of to the user. If you run ls -al and find that the permissions on .lotus are root:root then I would run chown and switch it to your user name for both:

```

sudo chown -R your_user:your_user ~/.lotus

```

---

### Post by ew1 on 2008-11-12
I've had fairly good luck with it.  On hardy I had a lot of problems with lotus notes 8.0.2 but it seems to be a lot more stable on intrepid.  After the initial install i deleted the 'default' /home/username/lotus folder and let it recreate it with the correct permissions upon first launch.  Also, it 'locks' up on me whenever anything happens to my network connection (network drops, connect to vpn, etc.) but after about a minute of it being locked up it usually comes out of it on it's own.  Other then that, my only problems was with the integrated sametime which I know have fixed.

---

### Post by kah00na on 2008-11-14
Where are the directions you guys are following to install this on Intrepid Ibex?  I keep finding directions on line but none of them seem to work for me.  I don't get the java window and end up using the "-console" option and that always has a lot of failures.

---

### Post by fenderek on 2008-11-19
> **ew1 said:**
> In case anyone runs into the same problem I had, I disabled the internal web browser inside of Lotus Notes, and told it to use my system default browser which fixed the problem with the integrated sametime client.

hi ew1, 
I'm having same problem with sametime. when I click on any user the chat window just doesn't open. I disabled the internal browser and it's set to use System Default one, still no go.  would you have any other suggestions ?
Thanks.

---

### Post by lunatico on 2008-12-04
Is there a Sametime installer for Ubuntu 8.10?
Or where can I get the installer for the whole Lotus Notes package? I looked for installing instructions on this forum but couldn'f find anything.
Thanks!

---

### Post by ew1 on 2008-12-04
Yes, there is a sametime installer for linux, but I had to get mine from our local ln admin (same for the whole ln package).  Another option would be you can always use pidgin to connect to sametime.

---

### Post by lunatico on 2008-12-04
Yes I'm using Pidgin at the moment, which for IM is fine. But we have several plugins and it would be nice if I could install them.
I don't think I'll get an installer for Ubuntu internally, only SUSE and Red Hat unfortunately. I tried converting the RPM to a DEB using alien but didn't work either.

---

### Post by ew1 on 2008-12-04
I'm not sure about the rpm, all I have ever been provided with was a tar  with a setup.sh install script for the lotus notes client.  I have not used the sametime client since 7.x which I also used alien on the rpm and it worked at that time.  Sorry I'm not of more help,

---

