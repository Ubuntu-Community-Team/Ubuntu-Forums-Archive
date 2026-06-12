---
title: "View images in CLI browser?"
date: 2008-07-21
forum: General Help
---

### Post by jerome1232 on 2008-07-21
Hey I'm currently limmited to my CLI only server, I'm using links2 to browse the web. I was just wondering if it's possible to get images to load using links2 or another (in the repos) CLI only browser.

Also is there a way to keep lynx from constantly asking me about cookies? I liked that one but I got sick of hitting 'y' ten times in a row.

---

### Post by meatpan on 2008-07-21
Probably more info than you want about cookies in lynx: [http://caunter.ca/README.cookies](http://caunter.ca/README.cookies)

I actually run 'lynx -accept_all_cookies', but this is not suggested.

Is there an x-server running on the server?  If not, it might be hard to get images unless you save and scp them to a machine running an x-server.

---

### Post by jerome1232 on 2008-07-21
No no x server, it's just host a teamspeak server for me and a few friends, and it only has 118 mb of ram, 400 mhz cpu so don't really want a x server. Thanks for the link that was helpful with lynx.

---

### Post by kaivalagi on 2008-07-21
Just installed "fbi", it's in the ubuntu repo's. Works a treat on the linux console and uses the frame buffer i.e. no X dependencies as far as I'm aware

Also found an article here (from 2006): [http://www.linux.com/articles/54158](http://www.linux.com/articles/54158)

Hope that helps :)

---

### Post by Vivaldi Gloria on 2008-07-21
> **kaivalagi said:**
> Just installed "fbi", it's in the ubuntu repo's. Works a treat on the linux console and uses the frame buffer i.e. no X dependencies as far as I'm aware

Also found an article here (from 2006): [http://www.linux.com/articles/54158](http://www.linux.com/articles/54158)

Hope that helps :)

Wow. Thanks mate. That's a great program. I have no X and it works great.

If only there was a cli webbrowser which used the frame buffer like that...

---

### Post by jerome1232 on 2008-07-21
fbi is awesome! thanks

---

