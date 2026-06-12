---
title: "Best way to exec program"
date: 2008-11-01
forum: General Help
---

### Post by martin0643 on 2008-11-01
I am looking for the best way to exec a program as root legitimately without having to result in trickery such as sticking an executable in the GDM startup scripts.  Here are the details:

1 Quad-Core Ubuntu-64 Box
1 Athlon XP 2400 Ubuntu-32 Box
Gigabit LAN

I am trying to run synergy between the two, and when I have the 32-Bit box as master and run the 64-Bit as slave, things run fine, but that's the opposite of what I am looking for.

When I run the 64-Bit as master and the 32-Bit as slave, when I mouse over there is massive stuttering and jumping and the cursor becomes hard to see or invisible.

I found I am able to correct this by running synergy client as root on the 32-Bit box, even though the 64-Bit daemon is running as a regular user.

I don't see an option to use the "sessions" dialogue box to enable superuser execution.  Obviously if I exec'd the command as "sudo synergyc" there would be no way to input the password, and this would most likely result in my password being in the clear in some file anyway.

I would normally (In OpenBSD or other SystemV setups) use the rc files to get things like this done, but since Ubuntu is moving away from that I would like to know a better way.  I tried using Upstart, and I managed to exec "synergy --daemon" that way, but when I use this method the daemon is unresponsive and will not allow the client to connect.

There must be a defined way to easily force all accounts to run a common program without the users themselves being able to access them and without them being closed when people login.

Bonus:  I would like to be able to have synergy available at boot to log into the machine so I could ditch the keyboard.  Is there an "approved" method of doing this without muching with the rc.local?  After login the process will be killed, but the sessions manager should be able to re-exec it at that point.

---

### Post by jpkotta on 2008-11-01
I have no experience with synergy.

I personally would either add it to /etc/rc.local, or run it with ssh.  There is a similar utility for X called x2x, but it seems more limited than synergy.  x2x needs no remote program other than an X server, however; I have used it with embedded systems and it worked very well.

---

