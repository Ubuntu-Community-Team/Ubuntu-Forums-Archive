---
title: "[SOLVED] Firefox .asp sites"
date: 2008-07-15
forum: General Help
---

### Post by nathanbosch on 2008-07-15
I have seen other threads referring to .asp sites and whether they are handled properly as html, however this issue is different.  When I try to access the site
[http://professional.osu.edu/opt.asp](http://professional.osu.edu/opt.asp)
it never loads. From what I've seen in other threads usually the page loads but the source is displayed, I can't even see the source for this page.  I have tried on 3 machines, all running Ubuntu Hardy with the same results.  When I tried the page in firefox on windows it displayed as expected. I don't think the windows box had upgraded to firefox 3 yet...(its my roomates laptop, I can find out if needed what version of firefox he runs)
Is this a firefox bug? is the server specifically blocking non windows os?

trying wget on this address results in
 --00:13:20--  [http://professional.osu.edu/opt.asp](http://professional.osu.edu/opt.asp)
           => `opt.asp'
Resolving professional.osu.edu... 128.146.108.180
Connecting to professional.osu.edu|128.146.108.180|:80... connected.
HTTP request sent, awaiting response... 

and it there it sits with a blinking cursor.
My roomate needs this site to apply for grad school, and I just convinced him to switch from windows.  Hopefully I can help him resolve this so he doesn't switch back!

**EDIT FIXED**
I found the solution to this problem, apparently it is a protocol issue (and yes, due to a poorly configured server)
if anyone runs into a similar problem (or is trying to access this same site)
to fix it temporarily:
echo 0 | sudo tee /proc/sys/net/ipv4/tcp_window_scaling
to fix it permanently:
edit the /etc/sysctl.conf
add line "net.ipv4.tcp_window_scaling=0"
test it after a reboot with "cat net/ipv4/tcp_window_scaling" and make sure it says 0

the permanent solution should be safe to make, although it may slightly slow down TCP on multi-gigabit networks

---

### Post by LaRoza on 2008-07-15
It doesn't work in Opera either. I would guess the server has sloppy code and the use of Linux makes it lock up (probably a poorly designed site) because there is no default condition.

---

