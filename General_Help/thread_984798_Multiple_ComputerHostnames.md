---
title: "Multiple Computer/Hostnames?"
date: 2008-11-17
forum: General Help
---

### Post by Nomel on 2008-11-17
Hey guys, I'm not sure in which section of the Forum to post this, so I'll just shoot out my question right here.

About a week or two ago, I installed Ubuntu 8.04 and after a couple of days I upgraded to 8.10. I was having issues with seeing windows computers from my network on both 8.04 and 8.10. I was messing around a little and finally got it to work.
Now, when I installed Linux, I used X as my Computer/Host-Name. After I got the Networking problem fixed, I changed the name to "Y", and restarted my computer. On the windows computers, however, I appeared still as "X". No big deal I figured, it'll just take some time...
When I checked my Network under Places, on my Linux box, i noticed that now both "X" and "Y" appear. Out of curiosity, I pinged both names, and for "Y" I got as expected the 127.0.0.1 as but for "X" I got some random IP somewhere many many miles away from where I live (I did an IP lookup...) Also, when I was pinging X, the console said:

```

PING "X"."Z" (IP of "X" here) 56(84) bytes of data.

```

where Z is the domain of the Network I'm in.

Now my question is, what the heck is going on here? :confused:
How come there appeared two computers in my network and why do I get someone from somewhere far away when I do an Ip lookup?

Hope this is not too confusing and hopefully someone can shed some light on this.

Thanks in advance :)

Edit: I also just realized, that one of the windows pc in my network appeared twice.. once under Network>Windows Network>Workgroup Name
and another time right at Network, where my linux machin is as well. This second appearance could also be traced back to the same IP that was referred to with the hostname X...
So a couple of minutes ago, I logged out and into another account to see if the second appearance of the windows pc could be found there as well (it's turned off..) but I could not find it there. I logged back into my other account and now it's not showing up there any more as well... 
What's going on here?

---

### Post by Peter09 on 2008-11-17
Can you confirm what IP schema you are using for your internal network.

---

### Post by Nomel on 2008-11-17
By IP scheme you mean like 192.168.2.1?

---

### Post by Peter09 on 2008-11-17
Yes - just to check it was valid. I guess the ability to ping outside of your domain means that:

1. Your router recognized that you missing machine was not part of the network so looked outside. Presume you pinged it by name?
2. Windows machines can take a long time to drop registered names.

Check what your router shows as connected. Most routers have a table that shows machines that are connected to them. Are you using DHCP?

---

### Post by Nomel on 2008-11-17
1. Yes, I was pinging by name.
2. It's not only for windows pc, but it was also for my own box.

I checked my router, but it doesn't show the name for my linux machine.. just the internal IP address..
Well, DHCP is enabled, but there is only one computer in the network using it.. all the others have manual addresses I think


I just noticed something by accident though. Whenever I use the ping command for any name, that is not in the network, it refers to that IP far away from me that I mentioned in my first post.

It doesn't matter what I put as a name so

```

ping xyz

```

and 

```

ping asdvgvdsgfgsdfsd

```

or any name pings that same computer 

this is the output:

```

PING atewyrdfgfesdfsfgh."My Domain Name here" (204.13.161.92) 56(84) bytes of data.
64 bytes from host204-13-161-92.oversee.net (204.13.161.92): icmp_seq=1 ttl=243 time=38.0 ms
64 bytes from host204-13-161-92.oversee.net (204.13.161.92): icmp_seq=2 ttl=243 time=41.0 ms

```

When I use the ping command on a windows box however, I get nothing...
I don't get it :confused:

---

### Post by Peter09 on 2008-11-18
Can you post the contents of your /etc/hosts file?

---

### Post by Nomel on 2008-11-18
```

127.0.0.1	linux-box	localhost.localdomain	localhost
127.0.1.1 linux-box.BASTLWASTL

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by iponeverything on 2008-11-18
Start using OpenDns servers in your /etc/resolv.conf

what is happening is that the DNS servers that you are using are routing all unknown resolution requests to the highest bidder.

[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by Nomel on 2008-11-18
Well, I changed the DNS in my /etc/resolv.conf file to the ones mentioned on [http://www.opendns.com/](http://www.opendns.com/), however I don't it changed anything.. (also on the site itself it stated that I'm not using OpenDNS..)

I suppose this is because I'm behind a router and I would have to change the settings for the router as well?

---

### Post by Peter09 on 2008-11-18
Yes, you should change your settings on the router.

---

