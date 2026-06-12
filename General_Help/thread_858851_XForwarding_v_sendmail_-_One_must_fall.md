---
title: "XForwarding v sendmail - One must fall"
date: 2008-07-14
forum: General Help
---

### Post by Tyconic on 2008-07-14
Hello all,

Recently I was trying to use X display forwarding from my Ubuntu desktop to my work computer (Os X 10.4), using

```
ssh -Y myself@mycomputer
```

Which failed at doing any forwarding, even though I get no Xauthority errors and checking the display gives

```
myself@mycomputer$ echo $DISPLAY
localhost:10.0 
```

```
myself@mycomputer$ xterm
xterm Xt error: Can't open display: localhost:10.0
```

This was very strange to me, as the same series of commands had previously worked like a charm. After cursing Steve Jobs for several minutes, I remembered that I had several days ago installed sendmail on my Ubuntu box, which came with its own issue: every time I started my computer, it would now hang for ~1-2 minutes, spinning the hard disks.

I was able to fix this by changing the first line of /etc/hosts from

```
127.0.0.1 localhost
```

to

```
127.0.0.1 localhost.localdomain mycomputer
```

... which unfortunately kills X forwarding :( My question is, may I have my X11 cake and eat it too, i.e. is there any way to have both X forwarding and a sendmail setup that doesn't hang my computer?

---

### Post by Tyconic on 2008-07-18
*bump*

---

### Post by dcstar on 2008-07-18
> **Tyconic said:**
> Hello all,

Recently I was trying to use X display forwarding from my Ubuntu desktop to my work computer (Os X 10.4), using

```
ssh -Y myself@mycomputer
```

........
```
127.0.0.1 localhost
```

to

```
127.0.0.1 localhost.localdomain mycomputer
```

... which unfortunately kills X forwarding :( My question is, may I have my X11 cake and eat it too, i.e. is there any way to have both X forwarding and a sendmail setup that doesn't hang my computer?

Firstly, I don't know why people use sendmail when postfix installs easily with little reported issues.......

Secondly, is "mycomputer" your machine's IP address or the remote address?

---

### Post by Tyconic on 2008-07-18
Hi dcstar,

This all started when I had to install bugzilla for a school project. Sendmail kind of tagged along as a happy coincidence.

"mycomputer" is a URL which resolves to my desktop's IP (I am using DynDNS since for most of the year I cannot count on having a static IP). I have no idea if it is correct to put it in the hosts file, like I said I got the idea from a forum post.

---

