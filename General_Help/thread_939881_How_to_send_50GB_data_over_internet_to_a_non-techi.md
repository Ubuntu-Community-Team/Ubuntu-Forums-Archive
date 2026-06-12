---
title: "How to send 50GB data over internet to a non-techie friend?"
date: 2008-10-06
forum: General Help
---

### Post by anil_robo on 2008-10-06
I'm using Ubuntu 8.04, and have a friend in another state. He left a hard disk with me by mistake, and it has 50GB data that he needs, though it's not urgent. Mailing him the hard disk is an obvious solution, but because both of us have high speed internet, I am thinking of sending him the data over the internet.

He uses windows vista, and his technical knowledge is very poor, but he can follow written instructions to click icons or menus.

Originally I was thinking of FTP, but then what if there is a disconnection? Probably the ftp client will ask to download all the data again? I'm afraid my friend may not be able to manage it.

I'm also thinking of bittorrent, but then I have no idea if it'll be effective if I'm the only peer serving the data, or how will I serup a tracker service.

Any hassle-free ideas on how to do this huge data transfer? Thanks in anticipation!

---

### Post by jms1989 on 2008-10-06
Maybe using a webserver on your end to serve up the files in zip files and he could download by using just his web browser? Of course, you'd need to forward port 80 and send him the web url to access your server. He could, then, use a download app that can resume downloads.

---

### Post by jerome1232 on 2008-10-06
50 GB is ALOT to move no matter how good your connection is, I wouldn't even move that over my lan. 50 gb = 429,496,729,600 bits, at 6000 bits per second (or 600 Kilobits per second) it'll take awhile, a long, long, long while.

That being said I'd use ssh. It's secure so the traffic is encrypted. 

[COLOR="Red"]edit: winscp can resume downloads.[/COLOR]

Your friend needs to download winscp (it has a easy to use point and click gui) [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

You just need the openssh server.
```
sudo apt-get install openssh-server
```

create a new limited account for him and put that data in it's home directory and he can copy it all to his machine.

---

### Post by patrickballeux on 2008-10-06
You could install a pptp server VPN supported by Windows) on your pc and share via Samba the HD.

So he will be able to access his data anytime until he gets is HD back...

You will need these packages:
- samba, system-config-samba (makes it easy to configure samba)
- pptpd
- an access in your firewall/router to access the PPTP server

Links:
[http://poptop.sourceforge.net/dox/debian-howto.phtml](http://poptop.sourceforge.net/dox/debian-howto.phtml)
[http://pigtail.net/nicholas/pptp/](http://pigtail.net/nicholas/pptp/)
This one is easy I think...
[http://swik.net/Ubuntu/Only+Ubuntu/Howto+setup+PPTP+server+(VPN)+on+Ubuntu+7.10/cdsjs](http://swik.net/Ubuntu/Only+Ubuntu/Howto+setup+PPTP+server+(VPN)+on+Ubuntu+7.10/cdsjs)


And is it useful in the future is you have other files to share.

Good luck!

---

### Post by cariboo on 2008-10-06
It would almost be just as fast to courier it overnight, especially as your friend is not very computer savvy.

Jim

---

### Post by estamand on 2008-10-06
I'm not sure what your ISP's montly cap on your data transfer is .. but 50GB might put you up there.

I aggree that courier is the most viable option.

---

### Post by jerome1232 on 2008-10-06
> **cariboo907 said:**
> It would almost be just as fast to courier it overnight, especially as your friend is not very computer savvy.

Jim

I think it most definitely will be faster, this would be an all day operation on a non-busy 100Mb LAN.

---

### Post by anil_robo on 2008-10-07
Thanks to everyone for replying. I have set up ssh on a non-standard port, and have sent my friend instructions for downloading using WinSCP. It'll take a few days, but I'm really excited over this project - never transmitted 50GB over the internet before! :)

---

### Post by Steve1961 on 2008-10-07
Hey, good luck :)  Let us know how this one turns out

---

### Post by fballem on 2008-10-07
> **anil_robo said:**
> Thanks to everyone for replying. I have set up ssh on a non-standard port, and have sent my friend instructions for downloading using WinSCP. It'll take a few days, but I'm really excited over this project - never transmitted 50GB over the internet before! :)

Aside from the joy at solving the technical problem, I have to wonder if this might be a case of: When you're up to your eyeballs in alligators, it's awfully hard to remember that the initial objective was to drain the swamp.

In other words, given a technical solution that requires several days, versus an overnight (or two-day courier), I suspect that it would have been better from the friend's perspective to receive the drive via courier.

Just a thought,

---

### Post by Steve1961 on 2008-10-07
> **fballem said:**
> Aside from the joy at solving the technical problem, I have to wonder if this might be a case of: When you're up to your eyeballs in alligators, it's awfully hard to remember that the initial objective was to drain the swamp.

In other words, given a technical solution that requires several days, versus an overnight (or two-day courier), I suspect that it would have been better from the friend's perspective to receive the drive via courier.

Just a thought,

Sure, but not as interesting!!

---

### Post by fballem on 2008-10-07
> **Steve1961 said:**
> Sure, but not as interesting!!

In other words, the objective changed and draining the swamp was no longer required!

---

### Post by jerome1232 on 2008-10-07
> **fballem said:**
> In other words, the objective changed and draining the swamp was no longer required!

Plus this way the OP get's a new drive!

---

