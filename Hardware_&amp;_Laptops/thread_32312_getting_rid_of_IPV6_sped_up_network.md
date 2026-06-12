---
title: "getting rid of IPV6 sped up network"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by whistl on 2005-05-07
I found that reconfiguring the kernel to removing IPV6 support sped up my network connections tremendously.

While a few people around the world might actually be using IPV6, I suspect the vast majority of us would prefer to have their DNS lookups and network connections run faster all the time.  Firefox, thunderbird, gaim - all start up and run much quicker now.

If you're getting tired of wondering why your web browser status line says "looking up www.whatever.com" for several seconds every time you click a hyperlink, try dumping IPV6.

---

### Post by bored2k on 2005-05-07
[QUOTE=whistl]I found that reconfiguring the kernel to removing IPV6 support sped up my network connections tremendously.

While a few people around the world might actually be using IPV6, I suspect the vast majority of us would prefer to have their DNS lookups and network connections run faster all the time.  Firefox, thunderbird, gaim - all start up and run much quicker now.

If you're getting tired of wondering why your web browser status line says "looking up www.whatever.com" for several seconds every time you click a hyperlink, try dumping IPV6.[/QUOTE]
 And just how did you reconfigured your kernel to remove ipv6?

---

### Post by whistl on 2005-05-08
You have to recompile the kernel from source code.  Not something non-programmers will be comfortable with, I'm sure.  I've been a UNIX programmer/system admin since the mid 80s, and using linux since version 0.99pl11, so recompiling a kernel is not a chore anymore.

I'm just a little surprised that the "standard" ubuntu kernel has IPV6 configured at all, considering it's negative impact on daily network performance.  I couldn't figure out how to turn off IPV6 using the "ifconfig" command, like you can in Solaris.  Maybe there is some other method that I'm not familiar with, something using /proc/.

I think the reason for the performance hit is mainly that if IPV6 is installed, every DNS lookup first attempts to find an IPV6 address, then if that fails, they attempt to lookup IPV4 addresses.  At least one of the websites I frequent apparently HAS an IPV6 address registered, so my system was doing IPV6 tunneled over IPV4 to reach it, which also slows performance down.

---

### Post by airhead on 2005-05-08
You don't need to recompile the kernel, as ipv6 support is loaded through a module. See this post: [http://www.ubuntuforums.org/showpost.php?p=90611&postcount=10](http://www.ubuntuforums.org/showpost.php?p=90611&postcount=10)

Rather than disabling ipv6, consider hopping on the ipv6 bandwagon. A tunnel is very easy to set up and once its done, you'll hardly ever need to touch it :) You won't even notice its there!

---

### Post by whistl on 2005-05-13
Thanks for the hint on easily disabling IPV6.

*Hop on the IPV6 bandwagon?*  Gee, the IPV6 bandwagon keeps circling round the block, but it never seems to get anywhere.  And it's blocking the road for the IPV4 city bus!

Seriously - what services can you reach with IPV6 enabled that cannot be reached with IPV6 disabled?  None.  Are IPV6 network connections any more secure, any faster, especially when tunneled over IPV4?  No.  So what's the point anyway?  With IPV6 enabled, **ALL** dns lookups are slower, meaning every click consumes more network bandwidth, and takes longer.  No gain, big penalty. so IPV6 loses.

Now, if some wonderful service comes along that requires IPV6, you be sure to let us all know, okay?  Until then, I see no reason for the added overhead and frustrating delays.

I attended an introductory class in IPV6 over 5 years ago, because our WAN team  fell for the hype, and anticipated a need.  We wanted to be prepared for when we HAD to support it.  I'm still waiting for a single application to be deployed that requires it.

---

### Post by nautilus on 2005-05-13
This is ridiculous.

Even without IPv6 support in the kernel, your applications STILL LOOKUP IPV6 HOSTS.

Sorry.  That speed boost you're feeling, if it is indeed the included IPv6 module, would be a severe bug in the Ubuntu distributed kernel.

Lookups are NOT done in the kernel, they are done by your C library, or by a library it references, but it simply never, ever, ever happens in the kernel.

Blindly crippling your kernel will not necessarily give a performance boost, despite the Gentoo mentality sweeping the Linux community.  Funny, because when you compiled a custom kernel and dropped your Ubuntu stock kernel, you saw a performance increase.

...I think that has more to do with the method, than with IPv6 support...

Custom kernels are typically faster than stock kernels for most of the appropriate reasons, but particularly: stock kernels are meant to be compatible, and custom kernels are meant to be compatible with **your system**, which allows you to enable all the tweaks and DMA you want.

...but maybe I'm just stupid.

As for the bandwagon, actually, IPv6 **is** more secure (even over a tunnel) and is **only** slower than IPv4 over tunnels.  You've missed a few key points, too, including integrated QoS capability (which is meaningless since Linux hasn't finished implementing it), and the inherited address space available, with a minor allocation of an 80-bit prefix, or, 2^48 address for personal use.

Hexago provides a 48-bit prefix, hurricane electric provides a 64-bit prefix.

Stick with that 640K ram mentality, I'm sure it's working for you.  We'll just move along and you can enjoy your busride.

---

