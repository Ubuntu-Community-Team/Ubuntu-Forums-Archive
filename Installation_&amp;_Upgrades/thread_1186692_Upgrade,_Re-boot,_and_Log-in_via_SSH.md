---
title: "Upgrade, Re-boot, and Log-in via SSH?"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by astroryan7 on 2009-06-13
I need to upgrade from Dapper to a newer version (perhaps 9.04), but I am half-a-world away from the actual machine.  So, I've been SSHing in.  My question is (and I've seen it partially answered in other posts, but not completely):  Can I upgrade from 6.06 to 9.04, re-boot to allow changes to take effect, and also log-in (at the normal username/password screen), via SSH?  And is this last step, the log-in part that I could not find answered in other posts, necessary via SSH, or will it log-in automatically after the re-boot?

I have root access.

Any pointers are appreciated, thanks!

---

### Post by expelledboy on 2009-06-14
I dont know how you would upgrade striaght from 6.06 to 9.04 but I do know that if you manage to upgrade your ssh login would still work as expected.

I just the other day ran a dist-upgrade on a server via ssh, rebooted, and logged straight back into the machine once I had given it time to start back up.

When you say will it login automatically what do you mean? On your side or at the server itself? It wont in both cases but that does stop you using any of the services provided by the server.

---

### Post by ducksun43 on 2009-06-14
yes, upgrade, issue **reboot **and two times** exit** (so you are logged out) ... wait 3 minutes or so to give the server time to reboot and log in as before

[http://sunoano.name/ws/public_xhtml/ssh.html](http://sunoano.name/ws/public_xhtml/ssh.html)

---

### Post by astroryan7 on 2009-06-14
Ok, great comments, thanks.  I just want to clarify, though, that this is a Desktop upgrade, not a Server upgrade.  Will that change your responses?  I can SSH in because my server admin has set up that particular tower (connected to a specific port) to the host server (i.e. it's [email]tower@tower.host.com[/email], for instance).

If I were standing at that tower and booting it up, I would normally have to log-in at the usual Ubuntu welcome screen, entering in a username/password.  I have the machine set to always stay logged-in; so, if I issue a

```
sudo shutdown -r now
```

command, will it forego that usual Ubuntu welcome screen, and just log back in, or will it get stuck there, waiting for someone to type the username/password?

And do you know if upgrading via

```
sudo apt-get dist-upgrade
```

will cause any problems over SSH?  I believe I have to go from Dapper -> Hardy -> Intrepid -> Jaunty.  Just unsure if there are any significant changes in that sequence that might affect upgrading via SSH and if I can even upgrade in this sequence using the above command.

I'm searching for this now...

Many, many thanks.

---

