---
title: "getting talkd to work in 8.04"
date: 2008-10-02
forum: General Help
---

### Post by jmeissen on 2008-10-02
I've searched the existing threads, and haven't see the correct solution to this.

I want to get talk to work on the local machine. I installed talkd_0.17-13_i386 and talk_0.17-13_i386. When I tried it I got Connection Refused. the logfile showed 

  "talk/udp: No such user 'nobody.tty', service ignored"

so I checked the /etc/inetd.conf file. The talkd and ntalkd entries had been added with a user field of 'nobody.tty'. So I changed it to just 'nobody' and restarted inetutils-inetd.

Now when I try I get "No connection yet", followed by "Checking for invitation on caller's machine", where it just hangs.

Any ideas?

---

### Post by hwertz on 2008-10-04
No, but I can give you a "me too".  I had one of my gentoo boxes hard disk crash recently; I really didn't feel like a 1-week reinstall :lolflag: so I threw Ubuntu on it.  I just reinstalled ytalk today (which pulls in talkd), just like you.  I changed nobody.tty to nobody, and now am getting errors similar to 
Oct  3 23:12:30 voltron talkd[13554]: recvfrom: bogus address length

     within /var/log/syslog
     It appears there are 4 bugs on bugs.ubuntu.com that are various forms of "talkd doesn't work in 8.04", "doesn't install in ibex", "ytalk doesn't work", etc.  I'm going to take a look at this for sure, I use ytalk a lot and I'd hate to have to do something kludgey like build talkd on my gentoo box and see if the binaries work.
     Edit: Check out Ubuntu bug 232051 at [https://bugs.launchpad.net/ubuntu/+source/inetutils/+bug/232051](https://bugs.launchpad.net/ubuntu/+source/inetutils/+bug/232051)   .  This is the bug "talkd doesn't work", and I'm going to post my progress there.

---

### Post by hwertz on 2008-10-04
In short, I changed /etc/inetd.conf to look like so:
talk            dgram   udp4    wait    root  /usr/sbin/in.talkd      in.talkd
ntalk           dgram   udp4    wait    root  /usr/sbin/in.ntalkd     in.ntalkd


     (Mind the word wraps of course).  I replaced "udp"s in the file with "udp4"s, it seems talkd was getting an IPV6 connection and taking a big dump on it.  And, I found running it as nobody, I had permissions problems so talkd could not notify users someone wanted to talk to them.  There *is* in fact a tty group, but it has no members by default.  Of course, you shouldn't run stuff as root, but I'm just not sure how to add extra permissions to the nobody account.

---

### Post by ways on 2009-04-01
that didn't work for me. when nmap'ing localhost i still have no open ports on 517/518. also the binary is called talkd, not in.talkd. i changed that. didn't help. tried using xinit.d with talk-file in /etc/xinetd.d/. no go. help?

/etc/xinetd.d/talk:

# default: off
# description: The talk server accepts talk requests for chatting with users \
# on other systems.
service talk
{
flags = IPv4
disable = no
socket_type = dgram
wait = yes
user = nobody
group = tty
server = /usr/sbin/talkd
}

---

### Post by genepool on 2009-06-25
I got it to work in Jaunty 32bit Desktop using the patch(s) in this _[[U]bug report_]("https://bugs.launchpad.net/ubuntu/+source/netkit-ntalk/+bug/250971")[/U].
Still can't get it working under Jaunty Server.

---

### Post by go_beep_yourself on 2010-11-06
> **hwertz said:**
> In short, I changed /etc/inetd.conf to look like so:
talk            dgram   udp4    wait    root  /usr/sbin/in.talkd      in.talkd
ntalk           dgram   udp4    wait    root  /usr/sbin/in.ntalkd     in.ntalkd


     (Mind the word wraps of course).  I replaced "udp"s in the file with "udp4"s, it seems talkd was getting an IPV6 connection and taking a big dump on it.  And, I found running it as nobody, I had permissions problems so talkd could not notify users someone wanted to talk to them.  There *is* in fact a tty group, but it has no members by default.  Of course, you shouldn't run stuff as root, but I'm just not sure how to add extra permissions to the nobody account.

You aren't supposed to "add extra permissions to the nobody account". You make the users you want belong to that group.

---

### Post by go_beep_yourself on 2010-11-06
> **ways said:**
> that didn't work for me. when nmap'ing localhost i still have no open ports on 517/518 <\SNIP>
}

Run nmap with sudo and -sU

---

