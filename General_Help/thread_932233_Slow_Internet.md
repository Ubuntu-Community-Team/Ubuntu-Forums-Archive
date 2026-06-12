---
title: "Slow Internet?"
date: 2008-09-28
forum: General Help
---

### Post by Hangwire on 2008-09-28
Hi,

Well I can see that my internet is a lot slower than on Windows XP. Ive compared them, the difference between loading pages is 10 to 15 seconds more, but my Download speed is the same and I have no problem with that.
I have done the IPv6 thing, no change.

Any Ideas?

Hardy Heron, Firefox 3.0

---

### Post by artships on 2008-09-28
"cat /etc/resolv.conf".  The first entry is probably the IP address of your router.  "sudo gedit /etc/resolv.conf" and remove that line and (and save the file) and see if the internet immediately gets faster.  If it does, "man resolver" to see how that file is built so that you can change how it's done.

---

### Post by Jeroensum on 2008-09-28
@artships  

If he does that and his router is the only nameserver he will get nowhere, which is very probable...

@Hangwire
The best thing to do is check the nameservers your router gets from your ISP and set those in the /etc/resolv.conf as the only nameservers, include the 'nameserver' statement infront of those IP's.
If this works, tell your router to forward the nameserver settings (you can probably set them in the DHCP tab on the router).

Also it might be that firefox is the problem, altough it's been rendering a lot faster than the last version (2.0.X.X) it's still not always up te speed on different systems. You might want to try other browsers like Opera or Epiphany.

---

