---
title: "Seamless rdesktop to a Windows domain"
date: 2008-09-12
forum: General Help
---

### Post by bartruji on 2008-09-12
I recently came across this on Digg:[ http://digg.com/linux_unix/Run_Windows_Apps_100_Seamlessly_on_Ubuntu?OTC-ig]("http://digg.com/linux_unix/Run_Windows_Apps_100_Seamlessly_on_Ubuntu?OTC-ig")

If the site is down try this: [http://img58.imageshack.us/img58/3867/mirrorui4.png]("http://img58.imageshack.us/img58/3867/mirrorui4.png")

I use the seamless feature of VirtualBox all the time and love it, but this article made me wonder if i can run seamlessrdp ([http://www.cendio.com/seamlessrdp/]("http://www.cendio.com/seamlessrdp/")) on a Windows Server 2003 Terminal Server.

So far im able to login and the menubar shows up on my ubuntu desktop, but right after the server's antivirus splash screen goes away the windows menubar disappears.

When i ran the command:

sudo rdesktop -A -s 'c:\seamless\seamlessrdpshell.exe c:\windows\explorer.exe' 168.xxx.xxx.xxx -u username -p password

i get this:
Autoselected keyboard map en-us
WARNING: Remote desktop does not support colour depth 24; falling back to 16
WARNING: ui_seamless_create_window: No parent window 0x10094
Segmentation fault

Nothing on google about the fault. 

Someone made the comment on the digg article that this wont work on a windows domain. Why not?

---

### Post by incudie on 2008-12-01
I can second this as being a problem in Intrepid with amd64.

Exact same error when opening windows.

Looks like this has been reported already.

[https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/275545]("https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/275545")

---

