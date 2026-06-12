---
title: "FireFox Slow in 9.10 Koala"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by opm595 on 2009-11-01
Hi Guys,

I've upgraded to 9.10 and I've noticed that FireFox is running painfully slow. I mean click on an URL and make a cup-of-coffee slow.
Just wondering if anyone has an answer to this. I simply upgraded from 9.04 to Koala via Update Manager, and everything else is running brilliantly as far as I can tell. 
Anyway, if someone can shed some light on this, it would be much appreciated.

Thanks in advance,
Rob

---

### Post by coldzero24 on 2009-11-02
the exact same thing happening to me i have no idea why??

---

### Post by ivan.bezyazychnyy on 2009-11-02
Hi!

I had the same problem. Then I found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757)

The advice to look [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/) help me (in my opinion the simplest of all dicisions I found).

---

### Post by ilpiero on 2009-11-02
> **ivan.bezyazychnyy said:**
> Hi!

I had the same problem. Then I found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757)

The advice to look [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/) help me (in my opinion the simplest of all dicisions I found).

Same problem here, Karmic fresh install I hope switching to opendns solves the issue.

---

### Post by opm595 on 2009-11-02
A million thanks, and much appreciated.
All running perfectly now!

Cheers,
Rob

---

### Post by Ithiel on 2009-11-03
If you are running a pentium machine with hyper-threading, turn the hyper-threading off in the machine's bios. Having had the same problem you are reporting on two machines, this has fixed the firefox issues on both of them.

---

### Post by soupowl on 2009-11-04
To OPM595 - can you say how you solved it, please?  It's driving me crazy.  I can't even get through to "about config" to change my settings!
Many thanks.

---

### Post by opm595 on 2009-11-04
Sounds like you might have a different problem at play, Soupowl.
In my situation I simply followed the instructions from the link that was posted here earlier and all was fine:
[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

Also as a suggestion, have you tried identifying your problem on Lauchpad, or filing a bug report? It sounds as if your problem may be a little different then what I experienced.

Best of luck,
Rob

---

### Post by jsimonelis on 2009-11-05
I have the exact same problem..
I just upgraded to ubuntu 9.10 running gnome and the new firefox 3.5 that was installed is SOOOOOOO slow.. I find it pretty much unusable.

Loading pages is slow.. It stalls on many pages that previously worked just fine.

We need to get this fixed ASAP.. I use this for work and I can't have this..

---

### Post by dragonetti on 2009-11-06
@[ivan.bezyazychnyy]("http://ubuntuforums.org/member.php?u=944326")
Thank you!

I had the same problem, it drove me nuts.
I didn't like the security policy (not able to remember the authentication) and the browsing was irritatingly slow.

Almost decided to go back to 9.04....almost....

Could somebody explain why the opendns setting makes browsing faster?

It's not perfect but way more tolerable.

---

### Post by Fire_Chief on 2009-11-06
It has to do with DNS lookups via IPv6 occuring before DNS lookups via IPv4. So the workstation (or app) has to timeout on the IPv6 request before it will make a new request on IPv4. OpenDNS gives an immediate response for the AAAA record query which eliminates the timeout problem.

At least that's what I think is happening after much reading on the problem.
Cheers!

---

### Post by Scallyph on 2009-11-06
[SIZE=2]Hi all,

I was just wondering..

If you right click on your network-icon (top right on your screen)
-choose &quot;edit connections&quot;
-select your active connection
-click on &quot;edit&quot;
-click on tab &quot;ipv6 settings&quot;
-In this new screen where it says &quot;Method&quot;
-if &quot;ignore&quot; is selected change it to &quot;automatic&quot;

I was just wondering ..
Does this improve your browsing/surfing experience/speed?

It worked for me until I rebooted computer.
After reboot I could not connect until I set ipv6 to "Ignore" again.
[/SIZE]

---

### Post by distortedecho on 2009-11-06
> **Scallyph said:**
> [SIZE=2]Hi all,

I was just wondering..

If you right click on your network-icon (top right on your screen)
-choose &quot;edit connections&quot;
-select your active connection
-click on &quot;edit&quot;
-click on tab &quot;ipv6 settings&quot;
-In this new screen where it says &quot;Method&quot;
-if &quot;ignore&quot; is selected change it to &quot;automatic&quot;

I was just wondering ..
Does this improve your browsing/surfing experience/speed?

It worked for me until I rebooted computer.
After reboot I could not connect until I set ipv6 to "Ignore" again.
[/SIZE]

Are you supposed to be using IPv6? Most people will be using IPv4.

I've changed to OpenDNS (used to have this configured into my router but had to remove it for a reason that now escapes me).

Regardless, this is a bug that needs addressing. Why would Firefox 3.5 be slower in 9.10.

Powers that be - please fix! :)

---

### Post by dragonetti on 2009-11-07
@[Fire_Chief]("http://ubuntuforums.org/member.php?u=350664")

Ok thanks!

---

### Post by Son of William on 2009-11-07
The OpenDNS fix worked for me.  I have a hard time understanding, however, how this got missed in beta.  Is this a problem for only a subset of machines?

---

### Post by Mickser_52 on 2009-11-08
I have just upgraded to 9.10 and am also finding Firefox very slow. The solutions being suggested seem to apply to Network manager but I have installed Wicd for my wireless suggestion. Can anyone tell me if there is a similar solution for this application.

---

### Post by Mickser_52 on 2009-11-09
I have fixed firefox problem by disabling ipv6 in firefox. Email and updating are still slow?

---

### Post by Fire_Chief on 2009-11-09
Yes, because your system is still attempting to make IPv6 DNS queries before IPv4 queries and it is causing timeout delays. If you follow the suggested action of using OpenDNS servers instead, your entire system will improve in speed on the Internet.

Cheers!

---

### Post by Mickser_52 on 2009-11-09
Thanks for your reply. The point of my first post was that the suggested instructions for opendns were for Networkmanager while I am using Wicd and am not sure how to go about configuring it.

Another point is that this was not necessary in 9.04 which worked well for internet. Is this to be a permanent change?

---

### Post by Fire_Chief on 2009-11-09
Here is a site that shows where to configure static DNS in wicd.
[http://wicd.net/screenshot.php]("http://wicd.net/screenshot.php")

I think you'd do well with either option (per connection/network configuration or global DNS servers setup).

Cheers!

---

### Post by OlympicSoftworks on 2009-11-11
This is only happening in a subset of machines whose internet connections at some point go through legacy equipment that is not IPv6 aware at all.  I get donations of computers, refurb them with Ubuntu and then give them away as part of my Non-Profit's charter.  I've installed 9.10 on 10 machines/laptops so far and network issues are nowhere among the few hickups I have seen so far.  At least here in Olympia, Washington with comcast as my ISP.

---

### Post by gupi-gupi on 2009-11-16
Took me a little to figure out, anyway the open dns solution did not work for me for some reasons, but then I noticed there is a ipv6 tag on the network manager configuration for auto eth0 (in my case) òust next to the ipv4 one, and there there is the cascade menu with the chice to ignore ipv6, this just fixed the issue right away.

---

### Post by marin123 on 2009-11-18
THANKS for the opendns solution!!!

all of my browsers took too long to load a web page, but downloaded at full speed, and when i changed my connection settings to opendns i was reborn :)
i tried firefox, chrome and opera and all the same... i also installed new flash player and JRE, but no result...

---

### Post by y0diggity on 2009-11-21
This didn't seem to do much for me (new DNS). I really notice this issue at the Verizon wireless site. It's ridiculously slow! I know it isn't my connection because when I go to a windows PC downstairs, it comes up immediately. I don't get it. I also have IPv6 disabled. 
I'm running 9.10.

Any more suggestions?

---

### Post by uboss on 2009-11-22
I was having the same problem so this is what I did just now and it really improved my speed. (Keep note of what you do in case you need to go back)

1. Type about:config in the address bar and press Enter
2. Then right click on the preferences table and select New->Integer
3. Type preference name as: **Network.dnsCacheExpiration** and Integer value **3600** (This will increase the DNS expiration cache time to 1 hour---you may decide the time you want)
4. Right click on the preferences table and select New.>Integer
5. Type preference name as: **network.dnsCacheEntries** and set its value between **100 to 1000** (By Default firefox has 20 entries I set mine at 400)
6. Type in the search and find each of the following and set their values as indicated below (Toggle will change the value like from false to true)

[B]network.prefetch-next  = true
network.http.pipelining  = true
network.http.pipelining.maxrequests  = 8
network.http.proxy.pipelining  = true
network.dns.disableIPv6  = true[/B]

7. Also right click and add another:  preference name as: **nglayout.initialpaint.delay** and set its value to **0**.

8. Plus I added the OpenDNS just as this thread mentions. 


Close the browser and restart. You are done.
I hope this helps

---

### Post by craig100 on 2009-11-22
The slowness I'm seeing is Firefox itself. When the mouse goes over something, a link, or the srcoll bar, it takes about 10 seconds for the link or scroll bar to be highlighted and become available to use.

Browser windows take ages to close too.

Also I get pauses in the response to the keyboard of the same order.

Anyone else see these?

Craig

---

### Post by uboss on 2009-11-22
What extensions are you using? disable all of them and and than re enable them one by one and see. Plus add these settings and see it might help. I was facing the similar problem but not that much. With me it was taking ages to just load a page or scroll through a page or clicking other tab would take a lot of time to change to that tab. It's been about 1 hour now I made these changes and it did improve. I think the most important is to disable the IPV6 Thing
**network.dns.disableIPv6  = true**

---

### Post by duds2008 on 2009-11-22
Thanks a million. Works like a charm! :) Opendns from now on!

---

### Post by gefalu2008 on 2009-11-25
After upgrading to Ubuntu 9.10 (64 bit) I also have experienced slow browsing with Firefox. I changed the ipv6 settings as advised but to no avail.

Then I tested Opera. That browser works fast. The difference is huge, and can be seen also when monitoring the performance of the network with the help of the Ubuntu performance monitor.

When using Opera in parallel with Firefox, the problem reappears. When closing Firefox, the problem disappears.

To my mind it seems that there is something wrong with Firefox or extensions (I use Xmarks.)

I like Firefox very much because of the extensions, so I hope the problem will be solved soon.

- Gef

---

### Post by marin123 on 2009-12-03
you dont have to add opendns servers...

you can find your dns server with "dig" command and edit your connection, this also works for me... using karmic with firefox 3.5.5...
if i dont type my dns servers then ubuntu chooses addresses of my wireless router(192.168.2.1) and my modem(192.168.1.1) (browsing the web takes ages)...

---

### Post by lsutiger on 2010-01-18
I wanted to reignite this thread as I just upgraded to 9.10 karmic and I tried all of the solutions in this thread and to be honest, it is now slower!

Has a true solution been found for this problem?

---

### Post by newseamus on 2010-01-19
> **ivan.bezyazychnyy said:**
> Hi!

I had the same problem. Then I found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757)

The advice to look [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/) help me (in my opinion the simplest of all dicisions I found).

thanks much...after trying a number of "fixes" your link actually sloved my problem.

---

### Post by lsutiger on 2010-01-19
I may need to change the DNS on our router also (this is for a work computer). Will report after I do that tomorrow.

---

### Post by spuudercat on 2010-02-08
OK I come from the time of dinosaurs and real slow browsers and mainly... in windows... so you'll have to excuse me if i'm right off the money here but i did find a good speed increase on my machine by disabling the proxy side of things in the browser

in IE way back it used to put the browser as "auto-detect" for the proxy, if you leave it on this it seems to query that there is a proxy there (which in my case I just have a simple straight-out connection) - the answer is "**NO-PROXY**"

anyway its disabled here and I seem to be functioning a hellish amount faster but as I say I am not a bunny and very much prior to Ubuntu was ..... a windows only chap!

nanoo nanoo

Garry

:popcorn:

---

### Post by 2hot6ft2 on 2010-02-13
Well for the last few days I've been doing a lot of reading about the IPV6 protocol. Disabling IPV6 in ubuntu. How to use it, who and where it's becoming implemented, as well as anything else I could about it and here's what I found in a nutshell.

Ipv6 used to be modular in ubuntu meaning you could just set it so the modules wouldn't load. Now it's built into the kernel and it's going to stay there. Any instructions you find for 8.10 wont work on 9.04 and up.

Countries like Japan are already well on their way in their efforts to deploying it, even offering subsidies to companies that deploy it's use.
The US Government is deploying it in the government systems.
Comcast is about out of IPV4 addresses and is looking for people to test their implementation of it.
Charter Communications does not have IPV6 DNS setup (I'm in that boat).

You can search for IPV6 with the name of your ISP and see if you can find out if they are deploying it or making any effort to make the change.

The USA seems to be dragging their feet on this and it's going to become the standard. Face it, we are just starting to feel the start of the transition.

Google is hard at work with IPV6 and I just bet that the reason the Google Chrome browser is fast is because it's configured to use IPV6. After all you can't really go into it's settings to see.

IPV6 has many improvements over IPV4 and it has the ability to be much faster. They really did a great job with how IPV6 works.

SECURITY: IPV6 packets can go right thru iptable since it's not designed to filter them (watched a you tube video of it being done). So now you'll have to start setting up ip6tables rules to filter them. Just run this and you'll see ubuntu already has the ip6tables built in as well as the IPV6 protocols:
```
grep icmp /etc/protocols
```
Do some searches and some reading on IPV6 for whichever part you're interested in. SSH allows all IPV6 Addresses by default, came as a surprise to me. You can ssh using it too.

I was trying to decide if I wanted to disable IPV6 or to make use of it instead and I would rather make use of it now.

I was considering the option of finding a IPV6 DNS server when I found this thread and making the changes suggested by uboss and the DNS changes has brought new life into firefox.

Here are a couple links on IPV6 if anyone is interested.
[Getting Around IPv6]("http://www.enterprisenetworkingplanet.com/netsp/article.php/3634596/Getting-Around-IPv6.htm")
[You-Tube-Understanding IPV6 Part 1]("http://www.youtube.com/watch#v=sKMvGIHXgBg&feature=related")

Thanks for the tips in this thread they have helped.

---

### Post by pyeager on 2010-03-09
As some other users have commented, I have seen slowness that is not explained by DNS performance.  I have also noticed that Firefox is using an inordinate amount of memory.

While the problem is the worst on a 1.2 G Pentium laptop with 256 M of memory (more is on order), this was not a problem with 9.04, and has become a huge problem with a fresh install of 9.10.

---

### Post by lsutiger on 2010-03-24
Bump...it is sooo sad to see firefox run sooo slow when I have a snappy computer :(

---

### Post by wkulecz on 2010-03-25
I saw this in 9.10 initially, but it seemed to go away after a few updates.

Its back with a vengence in 10.04Beta.  The network settings to disable IP6 don't seem to do anything, since they were set to "ignore" by default after installation, same as my 9.10 test system is.

---

### Post by norseman-has-a-laptop on 2010-03-25
ok im alil late to the party but did you try optmizing your browser?

---

### Post by lsutiger on 2010-03-26
> norseman-has-a-laptop

Do you mean all of the quick fixes in about:config?
Yes is the answer to that.
If not, what do you mean?

---

### Post by norseman-has-a-laptop on 2010-03-30
yes

---

### Post by khopek on 2010-04-06
The only thing that worked for me is killing my desktop.

By that I mean Alt+F2 then click on my desktop background.

Beause Ubuntu won't show previews of thumbnails in Wine apps...I have a nasty habit of saving to my desktop for ease of use.

Firefox goes SO slow it literally actually freezes and turns grey.

Killing my desktop brings the memory useage down to half.

---

