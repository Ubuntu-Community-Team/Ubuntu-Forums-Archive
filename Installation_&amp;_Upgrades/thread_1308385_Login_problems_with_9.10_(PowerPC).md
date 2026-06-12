---
title: "Login problems with 9.10 (PowerPC)"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by thamias on 2009-10-31
Hi
I've just installed 9.10 on my PowerMac G4, and everything seemed to go OK.
But when I restart for the first time and have to enter my username and password, my data are not recognized.
I've tried every possible combination with caps/non-caps, but it does not help.
I've even tried to reinstall the system 3 times with different usernames and passwords, but no luck

Am I misunderstanding something obvious?

Please help me out :-)

Best regards
Mathias

---

### Post by segomo on 2009-10-31
> **thamias said:**
> Hi
I've just installed 9.10 on my PowerMac G4, and everything seemed to go OK.
But when I restart for the first time and have to enter my username and password, my data are not recognized.
I've tried every possible combination with caps/non-caps, but it does not help.
I've even tried to reinstall the system 3 times with different usernames and passwords, but no luck

Am I misunderstanding something obvious?

Please help me out :-)

Best regards
Mathias


Hi Mathias!

I had the same problem on my iBook G4. It's an amazing bug (second time i've seen). The user you set-up at the install moment was no created  ¬_¬' 

So, here's the solution:

1.- In the step 2 of the Yaboot, press TAB to stop the automatic boot-loading (as default Linux)
2.- type this --> Linux nosplash rw init=/bin/bash
(This allow you to log-in as superuser (root) w/o any password at all!
3.- Then, let's create the user ---> adduser <username>
4.- And now, set it up as sudoer --> 

#visudo
-put this line at the end (replace username with your username):
username ALL=NOPASSWD: ALL

5.- And --> addgroup <username> sudo

Reboot and enjoy ;)

---

### Post by thamias on 2009-11-01
Hi there, and thanks a lot for your input!
I'm totally new to this - I was hoping that I could use this build of Ubuntu without touching the commandline. I must admit that being a Machead, this kind of stuff is VERY difficult to me :-)

Anyway, let's give it a try!
I came to step 4, but can you please tell me (in details) how to complete the last steps?

Again, thanks for your time and help - I really appreciate it!

Best regards
Mathias

---

