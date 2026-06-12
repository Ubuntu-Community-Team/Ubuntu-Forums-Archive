---
title: "Remote access returns error: &amp;amp;quot;X: user not authorized to run the X server, ab"
date: 2008-10-13
forum: General Help
---

### Post by abcuser on 2008-10-13
Hi,
on desktop computer I have Ubuntu 8.04 configured as headless server. On laptop I have Ubuntu 8.04.

Desktop is by default running without "X server". If I need graphics I start it by command "startx". X-server starts successfully without any error.

But if I try to do the same using remote laptop:
1. ssh -X userid@ip_of_desktop
2. startx
and second command returns error:
```
X: user not authorized to run the X server, aborting.
xinit:  Server error.
```
I can't quite understand if running commands within desktop using the same password as from remote laptop why I am not authorized to startx?

But if I start X on local desktop I can execute any graphic application on remote laptop (e.g. firefox).

The only problem is I can't start-up X-server remotely.

Directory .Xauthority on desktop has my userid privileges (read/write)

Regards,
Abcuser

---

### Post by fsdr78456987 on 2008-10-13
**Hack msn yahoo User name [http://www.pwhackers.webs.com]("http://www.pwhackers.webs.com") click on the GoogleAds on the bottom Marked back you will get the link in a few second if not go back and try again**

---

### Post by abcuser on 2008-10-13
Hi,
I figured out. On laptop I just executed firefox command without executing startx and Firefox starts on remote computer. I don't understand this but it is working.

I would like to understand. Can you please provide info to the following question: When "ssh -X userid@ip_remote_server" is executed where is X-server started?
1. On my laptop
2. On remote desktop computer

If now I understand correctly, X-server is started on my laptop? Is it?
Thanks

---

### Post by bodhi.zazen on 2008-10-13
what are the permissions of ~/.Xauthority on the server ?

ls -a to show them.

Try deleting this file and try forwarding x applications.

Generally it is best to forward single applications rather then the entire desktop. If you wish to forward the entire desktop use either a new x session of Xephyr.

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948")

---

### Post by ghij505 on 2008-10-13
[runescape](http://www.goldsrunescape.com)The famouse Blog [maple story](http://maplestory-mesos.blog.com)[maple story mesos](http://maplestory.blogs.experienceproject.com/)[Lotro Gold](http://lotro.weblog.com/)[runescape money](http://runescape-money.blog.com)I always read articles from these blog. Very excellent.The blogs about Runescape, Zezima, Loto, Cute Maple Story Online Game.

---

