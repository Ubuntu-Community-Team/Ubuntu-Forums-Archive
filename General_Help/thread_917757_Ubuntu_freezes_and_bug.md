---
title: "Ubuntu freezes and bug"
date: 2008-09-12
forum: General Help
---

### Post by ierpe on 2008-09-12
I am a web developer, so im running servers and servlets (apache, tomcat, php, mysql,...)
Firefox 3 has been buggy lately on my system, and it results sometimes in a "menu" freeze.
Everything seems to run normally except that the ubuntu menu bar (with applications, places, system..) freezes, i cant even access the stop button anymore...
And if i try to restart my serverX with ctrl+alt+backspace, it comes back normally to the login screen, i can login but then the session doesnt initialize...

Is there anything I can do to report the bug or to see logs of what is happening?

---

### Post by phidia on 2008-09-12
If you can't open System > Admin > Log Files from the top panel, and it sounds like you can't then you will need to look in /var/log/messages (also dmesg, syslog maybe others).

Maybe you can fix this with apt-get by getting a CLI (Alt+Ctrl+F1) then issuing "sudo apt-get update && sudo apt-get upgrade"  apt-get [reference]("http://doc.ubuntu.com/ubuntu/serverguide/C/apt-get.html")

---

