---
title: "jaunty - unable to access various websites"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by pompeyjohn on 2009-04-28
This is really wierd.

I have been working on this for most of the day, scoured this forum and googled the best I could. In desperation I now turn to you all. I hope someone can help.

So I installed jaunty 32 on a system that previously had vista running on it. [A sony Vaio laptop]. The install was a complete wipe of the drive. i.e. no shared partitions or multi-boot scenarios.

Upon logging into Ubuntu I run firefox and start some casual browsing. Some pages load fine, some just dont load at all. I get no error message, the page appears to be continuing to load - but nothing ever shows.

This also happens with Epiphany and Opera.

Here are three of the pages that are effected

[www.reddit.com](www.reddit.com)
[www.facebook.com](www.facebook.com)
[https://www.amazon.com/gp/sign-in.html](https://www.amazon.com/gp/sign-in.html)

So my first thought was that this was something to do with java/javascript. Just in case I installed the java binaries suggested in add/remove programs. After restart - no change.

My second thought was that this could be to do with ipv6. I have heard of issues with this protocol in the past so looked into disabling it. I am not sure I ever managed to successfully get it disabled despite following several guides on here. This could be the issue, and I am going to try and try again to disable ipv6 now. I really dont know enough about networking though to know if I am wasting my time going down this route though.

I have just confirmed that the router I am using linksys/cisco rv042 is not the issue as vista shows all those pages fine. I am running ubuntu LIVE from a USB pen drive at the moment.

What I am thinking is this *has* to be something low level in Ubuntu. I never had this problem with previous Ubuntu builds. Can anyone help me resolve this??

Many thanks in advance,
John

---

### Post by halovivek on 2009-04-28
HI 
Please check whether you have installed the flash player and ubuntu restricted extras has been installed in your system.
I had the same problem. I have reinstalled the ubuntu restricted extras and flash player and it is doing good now.

---

### Post by pompeyjohn on 2009-04-28
Thanks for the reply.

So I have gone ahead and installed to the hard drive so no longer running LIVE. All I have done since the install is to let the update manager run.

Also, I installed th extras and flash plugin that you suggested.

Problem remains :(

---

### Post by pompeyjohn on 2009-04-28
this is driving me crazy

---

### Post by alphacrucis2 on 2009-04-28
> **pompeyjohn said:**
> Thanks for the reply.

So I have gone ahead and installed to the hard drive so no longer running LIVE. All I have done since the install is to let the update manager run.

Also, I installed th extras and flash plugin that you suggested.

Problem remains :(

Do the sites that you can't connect to resolve? e.g from the terminal try

```
dig www.facebook.com
```

etc. dig will tell you at least if the names are resolving via the dns. By the Way I don't think this is a general jaunty problem as I haven't seen this before and it does work ok for me. Must be something specific to your setup.

---

### Post by pompeyjohn on 2009-04-28
Thanks alpha - here is the result of dig [www.facebook.com](www.facebook.com)

```
; <<>> DiG 9.5.1-P2 <<>> www.facebook.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23554
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;www.facebook.com.		IN	A

;; ANSWER SECTION:
www.facebook.com.	13	IN	A	69.63.184.143

;; AUTHORITY SECTION:
www.facebook.com.	90	IN	NS	glb01.ams1.tfbnw.net.
www.facebook.com.	90	IN	NS	glb01.sf2p.tfbnw.net.
www.facebook.com.	90	IN	NS	glb01.lhr1.tfbnw.net.
www.facebook.com.	90	IN	NS	glb01.ash1.tfbnw.net.

;; ADDITIONAL SECTION:
glb01.lhr1.tfbnw.net.	3337	IN	A	69.63.191.91
glb01.sf2p.tfbnw.net.	1084	IN	A	69.63.176.101
glb01.ams1.tfbnw.net.	3451	IN	A	69.63.191.219
glb01.ash1.tfbnw.net.	5331	IN	A	69.63.185.11

;; Query time: 16 msec
;; SERVER: 24.25.5.60#53(24.25.5.60)
;; WHEN: Tue Apr 28 03:28:17 2009
;; MSG SIZE  rcvd: 223
```

---

### Post by pompeyjohn on 2009-04-28
running firefox from the terminal generates no output on these pages

I know this might not seem like an installation issue - but this is on a completely clean vanilla install, and a machine I have proven works with previous ubuntu's.

---

### Post by alphacrucis2 on 2009-04-28
Well that's definitely not a dns issue then.

---

### Post by alphacrucis2 on 2009-04-28
Found this report. May be related:


[https://bugs.launchpad.net/ubuntu/+bug/367965]("https://bugs.launchpad.net/ubuntu/+bug/367965")

---

### Post by pompeyjohn on 2009-04-28
Thanks alpha, this is really appreciated

yeah that report looks similar.

initially i thought it was not a flash issue because I dont remember the amazon login process using flash.... but I guess there must be.

Well I have done complete removals and reinstalls of flashplugin-nonfree but nothing seems to have changed.

I have also just confirmed that this happens in seamonkey.

---

### Post by pompeyjohn on 2009-04-28
This could be irony - I cant get to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) either

---

### Post by alphacrucis2 on 2009-04-28
> **pompeyjohn said:**
> This could be irony - I cant get to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) either

I wonder why it works for me? My setup was installed at alpha 6 and I just installed the updates as they arrived so must be different in some way to a fresh install of the final release. Maybe a config file?

---

### Post by alphacrucis2 on 2009-04-28
Just a thought. Does the direct link work for you:

[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)")

---

### Post by evangotte on 2009-04-28
Hi
 
I had a similar problem to yours. I'm not sure if same websites were effected, but the ones I tried either had nothing displayed where Flash-player should be, or a big grey "Play" style button, which did nothing once clicked. 
 
After searching around, I found this blog:
[http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/](http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/)
which solved the problems I was having.
 
Let us know.
 
Evan

---

### Post by pompeyjohn on 2009-04-28
> **alphacrucis2 said:**
> Just a thought. Does the direct link work for you:

[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)")

nope that times out! Grrr

Do you know how to frame that as a wget? That could work

---

