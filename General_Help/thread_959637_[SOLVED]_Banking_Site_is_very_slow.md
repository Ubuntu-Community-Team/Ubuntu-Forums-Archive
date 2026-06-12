---
title: "[SOLVED] Banking Site is very slow"
date: 2008-10-26
forum: General Help
---

### Post by glantela on 2008-10-26
Hi Everyone,

I have a problem with my banking site, the Pcfinancial.ca login page is very slow.  I'm thinking it may be because of the new Java update from awhile back.  It used to work before that perfectly fine.  

I tried it on another computer and the website is fine.

Can anyone help me out?

Thanks

---

### Post by glantela on 2008-10-26
This is the actual URL, is anyone else having this problem with this particular site?

[https://www.txn.banking.pcfinancial.ca/a/authentication/preSignOn.ams?referid=loginBox_banking_go]("https://www.txn.banking.pcfinancial.ca/a/authentication/preSignOn.ams?referid=loginBox_banking_go")

---

### Post by uc50_ic4more on 2008-10-27
I have to second this. I am using Intrepid, and this has been persistently an issue from the beta on up to the RC. The site loads and works fine up until a login attempt is made -- It is the secure login and site that are painfully slow.

I have tried the site in Opera 9.5 on Intrepid and have encountered the same troubles. Using Safari 3.x and Firefox 3.01 on my MacBook Pro works flawlessly and quickly.

I have tried disabling extensions and plugins, but have noticed no change in performance so far.

---

### Post by hln on 2008-10-28
Thanks for posting this issue.  Indeed, I've also experienced very same problem since last Friday on my Open SuSE PC; I've also seen this problem posted on OpenSuSE forum.  I have OpenSuSE 10.3 with latest/greatest patches applied.  However, I have NOT seen this problem on my 2nd PC running XUBUNTU 8.04 (with all latest patches applied) nor on WinXP (my OpenSuSE PC is dual-boot).  In all case, I run FIREFOX 3.0.3 and I have not seen yet someone posted a solution or root-cause of this problem.  I will update all if I find something but hope this info is useful for evryone in solving this problem.

---

### Post by uc50_ic4more on 2008-10-28
hln -

1) Would you mind posting the URL for the OpenSUSE discussion pertaining to this problem? Perhaps there is something there that can help?

2) Is this issue *only* relevant to pcfinancial.ca, rather than other banking sites or sites with similar technologies? I wonder if they altered their technologies in a way that is rendering their site uncooperative with certain Firefox configurations. I remember canadiantire.ca not working on Opera 9 for a while before mysteriously rectifying itself. Regardless of how prevalent the issue is in terms of the number of sites that have become ultra slow in the last little while, is there a starting point for troubleshooting?

FWIW, I tried the site using IE6 in a virtualized WinXP (using Virtualbox 2.xx) on my Intrepid box, and the site was again ridiculously slow. Opera 9.5 and Firefox 3.xx on Intrepid are both slow, but Firefox, Safari 3.xx *and* IE6 on a virtual WinXP (Virtualbox 2.xx) on my Macbook Pro worked as quickly as one would expect.


> **hln said:**
> Thanks for posting this issue.  Indeed, I've also experienced very same problem since last Friday on my Open SuSE PC; I've also seen this problem posted on OpenSuSE forum.  I have OpenSuSE 10.3 with latest/greatest patches applied.  However, I have NOT seen this problem on my 2nd PC running XUBUNTU 8.04 (with all latest patches applied) nor on WinXP (my OpenSuSE PC is dual-boot).  In all case, I run FIREFOX 3.0.3 and I have not seen yet someone posted a solution or root-cause of this problem.  I will update all if I find something but hope this info is useful for evryone in solving this problem.

---

### Post by brydonhunter on 2008-10-28
I too am experiencing this problem. My Feeling is that PC Financial has done something to their site as both Ubuntu and Windows versions of Firefox 3 are causing the slowdown for me.

Hope it gets solved.

---

### Post by hln on 2008-10-28
uc50_ic4more,

1. OpenSuSE forum:

[http://forums.opensuse.org/network-internet/398436-please-help-i-cant-do-my-banking-anymore.html](http://forums.opensuse.org/network-internet/398436-please-help-i-cant-do-my-banking-anymore.html)

2. Good question.  Only pcfinancial.ca web exhibits this behavior.  Other bank like cibc.com and some secure sites with SSL connection/authentication such as aircanada.com, epost.ca, americanexpress.ca etc work flawlessly.

I will find sometime to run wireshark and compare my 2 PCs to see the difference and hopefully can shed some lights.  Did call PC Financial but guest the answer...  Our servers are running fine, I'm not aware of any changes, Oh, we don't support Linux...

---

### Post by sniperbob on 2008-10-29
I have the same issue, the site takes an excessive amount of time to load. It is not doing "nothing" while it is waiting, either. 

Looking at the system monitor: while it is sitting seemingly idle for several minutes just to load the login page,it has about 1kb/s down and 800b/s up, relatively constant.

It's not my connection.. I load other SSL pages and the down speed goes up to over 200kb/s for less than a second, the page loads, all is well.

Anyone come up with anything on this yet?

---

### Post by eclindholm on 2008-10-29
Hi  there.

I am the originator of the opensuse forum thread.

In a way I am glad that I am not the only one with this issue as I am at somewhat of a loss on what to do.

I have looked at wireshark as well, and the packets are tiny...in the 100byte per packet. also the data stream seems fairly consistant but has a ~100ms turn around per packet on their end. This is way to long. I will look from my work machine and compare

Craig

---

### Post by hln on 2008-10-29
Craig,

If possible, can you post your wireshark capture (pcap file) so that someone/SME reading this forum can help and extract more useful data for troubleshooting this problem?  (I realize you've gone through this but the more people putting their heads together, the better...)

---

### Post by glantela on 2008-10-29
I just tried the site right now on WinXP Firefox 3.03, and it works as normal... I had thought it was Java, but i'm using the same version (JRE 1.6.0_03) on this machine so i guess its not that...

---

### Post by hln on 2008-10-29
Thanks glantela for confirmation on my observation using Firefox on WinXP reported yesterday (works normally).  By the way, I've also tried Konqueror browser on my OpenSuSE 10.3 and the same issue is observed (slow to display the log-in page).  Allow me to re-iterate again that Firefox on XUBUNTU 8.04 works well.

---

### Post by footman_75 on 2008-10-30
Same problem.  Just got kicked off my PCFinancial account page due to a session "time-out."  That's how long it's taking!

Please everyone contact PCFinancial with email registering this complaint.

---

### Post by KrazyPenguin on 2008-10-31
hey, me and my wife are getting same problem for about 2 weeks now.

i've got laptop running ubuntu 8.10 and she has laptop running 8.04.

no diff 


anybody try it with virtualbox running XP or xubuntu??

could be some kind of firewall issue, not sure!!!

---

### Post by KrazyPenguin on 2008-10-31
oh, and one more thing.

mybell.ca does the same thing, but even slower sometimes, wondering if it is the same technology??

---

### Post by Spoom on 2008-10-31
I never realized that this was specific to Linux.  I'm on Intrepid AMD64 and having the same issue.  It always seemed to me like a server problem, since the delay seems to happen in loading and not anything client-side.  Has anyone tried changing their user agent to appear to be Windows?

Same thing on bell.ca (which is actually a lot worse).

---

### Post by grant.guenther on 2008-10-31
> **glantela said:**
> Hi Everyone,

I have a problem with my banking site, the Pcfinancial.ca login page is very slow.  I'm thinking it may be because of the new Java update from awhile back.  It used to work before that perfectly fine.  

I tried it on another computer and the website is fine.

Can anyone help me out?

Thanks

I'm not a Ubuntu user, but I found this thread while trying to resolve the same problem with Fedora 9.   Seems there's a tcp option that the PCFinancial server does not like.   Try:

echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

(or set it in /etc/sysctl.conf).

Works for me, anyway.

---

### Post by drg006 on 2008-10-31
> **grant.guenther said:**
> I'm not a Ubuntu user, but I found this thread while trying to resolve the same problem with Fedora 9.   Seems there's a tcp option that the PCFinancial server does not like.   Try:

echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

(or set it in /etc/sysctl.conf).

Works for me, anyway.

Brilliant!  Thanks :)

---

### Post by sniperbob on 2008-10-31
Worked like a charm, thank you thank you :guitar:

---

### Post by miscellanyous on 2008-10-31
> **grant.guenther said:**
> I'm not a Ubuntu user, but I found this thread while trying to resolve the same problem with Fedora 9.   Seems there's a tcp option that the PCFinancial server does not like.   Try:

echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

(or set it in /etc/sysctl.conf).

Works for me, anyway.

Thanks for this. I am still having a little trouble. I have noticed a slow connection to pcfinancial.ca for a week or two.

**My system:** KDE 3.5.10  /  Kubunutu 8.04.1
**browser:** Firefox 3.03

OK, to the problem,
```
chris@csHome:~$ cd /proc/sys/net/ipv4/

chris@csHome:/proc/sys/net/ipv4$ sudo tcp_window_scaling
sudo: tcp_window_scaling: command not found
```


I also observe all the files in /proc/sys/net/ipv4/ are of size 0 bytes. Is that normal?

Lastly, I include my /etc/sysctl.conf
```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.  (Added in kernel 2.6.22.)
kernel.maps_protect = 1

# Increase inotify availability
fs.inotify.max_user_watches = 524288

# protect bottom 64k of memory from mmap to prevent NULL-dereference
# attacks against potential future kernel security vulnerabilities.
# (Added in kernel 2.6.23.)
vm.mmap_min_addr = 65536

##############################################################3
# Functions previously found in netbase
#

# Comment the next two lines to disable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling (http://lkml.org/lkml/2008/2/5/167)
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.ip_forward=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net/ipv4/icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net/ipv4/icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net/ipv4/conf/all/accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net/ipv4/conf/all/secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net/ipv4/conf/all/send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net/ipv4/conf/all/accept_source_route = 0
#
# Log Martian Packets
#net/ipv4/conf/all/log_martians = 1
#
# Always defragment packets
#net/ipv4/ip_always_defrag = 1

```

There is no property to enable/disable tcp_window_scaling. Where do I find this?

And lastly, why does the pcfinancial.ca secure site require this to be disabled? Sorry for all the questions! :)

---

### Post by valyok on 2008-10-31
Hey, guys!

I am ...guess what ...having the same problem you all got!

I have been trying to communicate the problem to PC Financial "Tech Support" for more than a week now.
So just 5 minutes ago I got off the phone with them and they said that they will forward the problem description to the actual tech support guys.
One interesting thing is - they say not one person called with the same problem before.

SO - why don't all of you guys call them and tell about the problem so that there's more than one person. I hope then they will take the request seriously.
So I called 1-888-723-8881, then key in your card number, then choose options 5,1,3.

Let me(us) know what their response is.
Some people I talked to on the phone in the course of 7-10 days were absolutely dismissive of the problem...

cheers

---

### Post by grant.guenther on 2008-11-01
> **miscellanyous said:**
> Thanks for this. I am still having a little trouble. I have noticed a slow connection to pcfinancial.ca for a week or two.

**My system:** KDE 3.5.10  /  Kubunutu 8.04.1
**browser:** Firefox 3.03

OK, to the problem,
```
chris@csHome:~$ cd /proc/sys/net/ipv4/

chris@csHome:/proc/sys/net/ipv4$ sudo tcp_window_scaling
sudo: tcp_window_scaling: command not found
```


I also observe all the files in /proc/sys/net/ipv4/ are of size 0 bytes. Is that normal?

Lastly, I include my /etc/sysctl.conf
```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.  (Added in kernel 2.6.22.)
kernel.maps_protect = 1

# Increase inotify availability
fs.inotify.max_user_watches = 524288

# protect bottom 64k of memory from mmap to prevent NULL-dereference
# attacks against potential future kernel security vulnerabilities.
# (Added in kernel 2.6.23.)
vm.mmap_min_addr = 65536

##############################################################3
# Functions previously found in netbase
#

# Comment the next two lines to disable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling (http://lkml.org/lkml/2008/2/5/167)
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.ip_forward=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net/ipv4/icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net/ipv4/icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net/ipv4/conf/all/accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net/ipv4/conf/all/secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net/ipv4/conf/all/send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net/ipv4/conf/all/accept_source_route = 0
#
# Log Martian Packets
#net/ipv4/conf/all/log_martians = 1
#
# Always defragment packets
#net/ipv4/ip_always_defrag = 1

```

There is no property to enable/disable tcp_window_scaling. Where do I find this?

And lastly, why does the pcfinancial.ca secure site require this to be disabled? Sorry for all the questions! :)

(1)  /proc/sys/net/ipv4 is a virtual directory, each file therein corresponds to a live configuration setting in the kernel.   By reading (with cat) or writing (with echo >) those files you can change the kernel's behaviour on the fly.

(2)  So, su to root and then execute the command I gave above, exactly:

echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

that will write 0 into the parameter and disable the window scaling option.

(3)  to make this permanent, you would add 

net.ipv4.tcp_window_scaling = 0

into /etc/sysctl.conf

(4)  of course, there may be other ways of editing that file - this is the generic method.

G.

---

### Post by grant.guenther on 2008-11-01
> **valyok said:**
> Hey, guys!

I am ...guess what ...having the same problem you all got!

I have been trying to communicate the problem to PC Financial "Tech Support" for more than a week now.
So just 5 minutes ago I got off the phone with them and they said that they will forward the problem description to the actual tech support guys.
One interesting thing is - they say not one person called with the same problem before.

SO - why don't all of you guys call them and tell about the problem so that there's more than one person. I hope then they will take the request seriously.
So I called 1-888-723-8881, then key in your card number, then choose options 5,1,3.

Let me(us) know what their response is.
Some people I talked to on the phone in the course of 7-10 days were absolutely dismissive of the problem...

cheers

Don't bother - I called them yesterday too - they told me there were aware of a similar issue with Mac OS.  

I also tried running IE under XP under VMware and got the same problem, so I concluded that this must be a conflict between the host OS TCP stack and the PCF server's TCP stack.   I did some tcpdumps and noticed the window scaling option and tiny windows, so decided to try turning off window scaling, and it worked.

Try disabling window scaling (see earlier posts) and see if that fixes your problem.

G.

---

### Post by valyok on 2008-11-01
I know.
That's why when I spoke to a person like you describe - I just hang up and called again and spoke to a different person.

Valera

> 
    valyok,

    As mentioned in my previous post, I did call them but they don't want to hear anything but Windows!

    Liem


---

### Post by petervk on 2008-11-01
This solved it for me:

```
sudo -s
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```

Add this to bottom of /etc/sysctl.conf

```

# fix stupid pcfinancial site
net.ipv4.tcp_window_scaling = 0
```

---

### Post by KrazyPenguin on 2008-11-01
Just confirming the fix works for PC Banking!!!!!!!

It has also sped up mybell.ca, which was very slow for a long time!!!

:guitar:

---

### Post by valyok on 2008-11-01
THNX a lot for the fix!
I should have read the thread more carefully!

V

---

### Post by alienprdkt on 2008-11-01
> **valyok said:**
> Hey, guys!

I am ...guess what ...having the same problem you all got!

I have been trying to communicate the problem to PC Financial "Tech Support" for more than a week now.
So just 5 minutes ago I got off the phone with them and they said that they will forward the problem description to the actual tech support guys.
One interesting thing is - they say not one person called with the same problem before.

SO - why don't all of you guys call them and tell about the problem so that there's more than one person. I hope then they will take the request seriously.
So I called 1-888-723-8881, then key in your card number, then choose options 5,1,3.

Let me(us) know what their response is.
Some people I talked to on the phone in the course of 7-10 days were absolutely dismissive of the problem...

cheers

I am not a member but have wrote them an email regarding this and this was there reply:

[FONT=Century Gothic][SIZE=2][COLOR=#000000]Thank you for taking the time to write President's Choice Financial.  
 
To access online banking, you need a browser with a minimum of 128-bit encryption. President's Choice Financial works with a 128-bit encrypted browser version of: 
 
Using Microsoft Windows 
 
- Microsoft Internet Explorer 5.5 or higher 
- Netscape Navigator 6.2 or higher 
 
Using Macintosh OS 
 
- Microsoft Internet Explorer 5.2.3 
- Apple Safari 1.0 or higher  
 
For tips on upgrading your browser, please visit [http://www.banking.pcfinancial.ca/a/security/whatWeDo.page#more_secure_browsers](http://www.banking.pcfinancial.ca/a/security/whatWeDo.page#more_secure_browsers) 
 
Thank you for visiting [www.pcfinancial.ca]("http://www.pcfinancial.ca/"). 
 
 
Sincerely, 
 
Curtis 
Internet Communications Specialist 
 
---------------------------------------  
Note From President's Choice Financial services e-mail Postmaster: For reasons of security and confidentiality, some information in your original communication may have been altered. This information is marked by X's or . 
---------------------------------------  
This information is confidential and for the exclusive use of the person to whom it is addressed. If you are not the intended recipient, please advise us by e-mail and destroy or return to us any copies. President's Choice Financial services are provided by the direct banking division of CIBC. CIBC accepts no liability for use by third parties or for errors or omissions. 
 



It appears that they don't support linux, or firefox. there web developer really sucks!
[/COLOR][/SIZE][/FONT] [FONT=Arial][SIZE=1][COLOR=#ffffff] TRACKING NUMBER: A00002790398-00008621257 [/COLOR][/SIZE][/FONT] [FONT=Arial][SIZE=2][COLOR=#000000] 
 [/COLOR][/SIZE][/FONT]

---

### Post by glantela on 2008-11-01
It works! I will mark it as SOLVED.

Thanks for everyone's help!

---

### Post by TheDoctorWho on 2008-11-02
ISSUE:
When accessing [https://www.txn.banking.pcfinancial.ca/a/authentication/preSignOn.ams?referid=loginBox_banking_go](https://www.txn.banking.pcfinancial.ca/a/authentication/preSignOn.ams?referid=loginBox_banking_go)

The page comes up very slow. Once logged in response remains slow.

ENVIRONMENT
Ubuntu 8.04 and 8.10
Firefox 3.0.3 (Investigation finds this to be a problem for version 2.x as well)

CAUSE
tcp_window_scaling is set to true (1)

RESOLUTION
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

PROBLEM
When you reboot the machine, you get the same problem.
tcp_window_scaling goes back to 1

WHAT I DID to fix the problem:

Set echo 0 > /proc/sys/net/ipv4/tcp_window_scaling into rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
exit 0

HOW to do this?
Could use vi or pico

EXAMPLE:
sudo pico /etc/rc.local
Enter password
Make change
Exit with save.

---

### Post by stephanecharette on 2008-11-07
This company has been so difficult to deal with!  For 2 weeks I've been calling, and they keep telling me no-one else has reported any problems, everything is working just fine, and by the way, we only support Windows.

<sigh>

Thanks for all the hints in this thread.  Wish I had thought of looking it up sooner.  This solved the problem for me:
```
sudo -i
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```

I'll try and call again and let them know.  Obviously they must have recently inserted into their network some device that isn't dealing very well with the tcp window scaling option.

Thanks again.

Stéphane Charette

---

### Post by uc50_ic4more on 2008-11-07
Stéphane -

Thanks! That command worked perfectly over here. Would you mind taking a moment, though, to explain what the heck we just did with the command? What is TCP window scaling and is there peril elsewhere on the interweb in disabling it? I found some info here: [http://en.wikipedia.org/wiki/TCP_window_scale_option](http://en.wikipedia.org/wiki/TCP_window_scale_option), but I am having some difficulty comprehending it as a layperson.

As well, my wife and I have called PC Financial a few times about this issue, with varying degrees of politeness, and were told pretty much the same thing(s). I suppose having our displeasure voiced and on record somewhere is the best thing we can do at this point.

Thanks, again!

> **stephanecharette said:**
> This company has been so difficult to deal with!  For 2 weeks I've been calling, and they keep telling me no-one else has reported any problems, everything is working just fine, and by the way, we only support Windows.

<sigh>

Thanks for all the hints in this thread.  Wish I had thought of looking it up sooner.  This solved the problem for me:
```
sudo -i
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```I'll try and call again and let them know.  Obviously they must have recently inserted into their network some device that isn't dealing very well with the tcp window scaling option.

Thanks again.

Stéphane Charette

---

### Post by stephanecharette on 2008-11-07
> **uc50_ic4more said:**
> Would you mind taking a moment, though, to explain what the heck we just did with the command? What is TCP window scaling and is there peril elsewhere on the interweb in disabling it?

Oversimplified explanation of tcp window scaling:

When packets are transmitted between your computer and the web server, there is something called a "window size" which the computers use to tell each other just how much data they can take at once.  Oversimplified again:  this is to prevent servers from flooding clients with data faster than what they can process.

Because all of this was invented many years ago, the maximum "window size" is no longer optimal for today's networking speeds.  So a sliding window scale means the computers can say "my window size is 10", but the scaling option will say "but multiply that number by 100".  The problem is, a device on the PC Financial network (most likely a gateway/router, but possibly the web server itself) is saying it supports tcp window scaling, but not doing the right thing.  Instead of taking the 10 and multiplying it by 100, it thinks "10" is the amount of data your computer can take at once.  So it sends many small packets.  The data is broken down so much, it takes 30 minutes just to get the login page to show up.

By disabling window scaling, you are somewhat limiting the network capability of your computer, but you're limiting it the same way it would be limited when communicating with any server that does not support the tcp window scaling option.

Hope this helps.

Stéphane Charette

---

### Post by uc50_ic4more on 2008-11-07
Stéphane -

An oversimplified explanation is *exactly* what I was after! Thanks...

Regarding the potential less-than-optimal networking setup we have now, after disabling TCP window scaling, can the process be reversed by using the same command but using "1" instead of "0"?

> **stephanecharette said:**
> Oversimplified explanation of tcp window scaling:

When packets are transmitted between your computer and the web server, there is something called a "window size" which the computers use to tell each other just how much data they can take at once.  Oversimplified again:  this is to prevent servers from flooding clients with data faster than what they can process.

Because all of this was invented many years ago, the maximum "window size" is no longer optimal for today's networking speeds.  So a sliding window scale means the computers can say "my window size is 10", but the scaling option will say "but multiply that number by 100".  The problem is, a device on the PC Financial network (most likely a gateway/router, but possibly the web server itself) is saying it supports tcp window scaling, but not doing the right thing.  Instead of taking the 10 and multiplying it by 100, it thinks "10" is the amount of data your computer can take at once.  So it sends many small packets.  The data is broken down so much, it takes 30 minutes just to get the login page to show up.

By disabling window scaling, you are somewhat limiting the network capability of your computer, but you're limiting it the same way it would be limited when communicating with any server that does not support the tcp window scaling option.

Hope this helps.

Stéphane Charette

---

### Post by stephanecharette on 2008-11-07
> **uc50_ic4more said:**
> after disabling TCP window scaling, can the process be reversed by using the same command but using "1" instead of "0"?

If you only do the steps I mention above, then either a reboot, or as you say using 1 (one) will restore tcp window scaling.

Some of the other posts in this thread mention changes to make this persist after a reboot.  You'd have to revert those changes to go back to the linux default value of supporting scaling window sizes.

I plan on just running the command I wrote above when I want to access the PCFinancial site.  Next time I reboot, if PCFinancial hasn't fixed it, I'll run the command again, etc...  At some point, this will work again even with the tcp window scaling option enabled.

I've spoken to them several time today to discuss the problem -- I'm hoping that since they've now been told the cause, they'll remove/replace the offending device off their network, or have a fix available soon.

Stéphane Charette

---

### Post by uc50_ic4more on 2008-11-07
Stéphane

Right on! Thanks a bunch for 1) posting this fix, 2) explaining it, and 3) interfacing w/ the folks @ PC Financial --  You're a credit to the community.

> **stephanecharette said:**
> If you only do the steps I mention above, then either a reboot, or as you say using 1 (one) will restore tcp window scaling.

Some of the other posts in this thread mention changes to make this persist after a reboot.  You'd have to revert those changes to go back to the linux default value of supporting scaling window sizes.

I plan on just running the command I wrote above when I want to access the PCFinancial site.  Next time I reboot, if PCFinancial hasn't fixed it, I'll run the command again, etc...  At some point, this will work again even with the tcp window scaling option enabled.

I've spoken to them several time today to discuss the problem -- I'm hoping that since they've now been told the cause, they'll remove/replace the offending device off their network, or have a fix available soon.

Stéphane Charette

---

### Post by stephanecharette on 2008-11-10
Got an e-mail from "Fabienne", with the ironic title of "Internet Communications Specialist" at PC Financial.  Looks like very little will be done about this:

> Dear Sir or Madam,

Thank you for taking the time to write President's Choice Financial. Please note that we are currently experiencing a higher than usual volume of correspondence and accordingly, our response time is greater than usual. We apologize for any inconvenience this may have caused you and thank you for your patience.

Unfortunately, the combination of browser and operating system that you are using is not supported by President's Choice Financial online banking.

To access online banking, you need a browser with a minimum of 128-bit encryption. President's Choice Financial works with a 128-bit encrypted browser version of:

Using Microsoft Windows

- Microsoft Internet Explorer 5.5 or higher
- Netscape Navigator 6.2 or higher

Using Macintosh OS

- Microsoft Internet Explorer 5.2.3
- Apple Safari 1.0 or higher


You may find that you can access Online Banking using various non-supported browsers and/or operating systems, however support is not available.

We apologize for any inconvenience this may cause you.

Thank you for visiting [www.pcfinancial.ca](www.pcfinancial.ca).

At least we have an easy-to-use workaround.

Stéphane Charette

---

### Post by stoian on 2008-11-11
I have been looking for weeks for a fix, whew!
(running Ubuntu 8.04 and Firefox 3.03)
I can confirm that this fix made it. (see petervk's post on page 3):

Quote:
----------------------
This solved it for me:


```
sudo -s
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```

Add this to bottom of /etc/sysctl.conf

```
# fix stupid pcfinancial site
net.ipv4.tcp_window_scaling = 0
```

------------------------------------------

Thanks a lot!

---

### Post by slyyls on 2008-11-12
Just for information.  My laptop is currently running gentoo, and I have window scaling set to 1.  I don't have this problem.  My wife is using Ubuntu and does have this problem.

The big differences I see are Ubuntu has a new Kernel and firefox3.  I have read there was a cleanup in the new 2.6.27 kernel regarding TCP.  It might be related to that.  Can other non-ubuntu users having this problem confirm this?

---

### Post by stephanecharette on 2008-11-12
> **slyyls said:**
> I have read there was a cleanup in the new 2.6.27 kernel regarding TCP.  It might be related to that.  Can other non-ubuntu users having this problem confirm this?
On page 1 of this thread is an OpenSUSE user with this problem, and on page 2 is a Fedora Core 9 user.  FC9 is recent, OpenSUSE user didn't leave us with the version number.

The problem has also been reported from users with Opera, so it wouldn't be specific to FF.

And when I use Internet Explorer or FF from within a Vista VirtualBox running in Ubuntu 8.10, I also experience this problem.  So I'm guessing anyone who has a linux-based NAT firewall could potentially experience this issue regardless of what OS they run on their desktop/laptop.

Here is a [link]("http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/") where this problem is discussed back in August 2006.  Note the links to existing discussion about this on the LKML (linux kernel mailing list).  It also has this great prediction:> Now when most big distros move to kernel 2.6.17 (just in the next month or 2) we&#8217;ll have thousands of people complaining that their connection doesn&#8217;t work. And nobody will know or care about window scaling.

Of particular interest is this one, from July 7 2004:  [http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/)

Stéphane

---

### Post by tom17 on 2008-11-15
Wow, never thought to actually check to see if others had this problem. I just did my PC Financial banking at work for the last few months.

Great thread. My PCF is now working with this "bodge".

Now, on to the crux of the matter. I work in the field of networking and hosting so read up about TCP Window Scaling and understand it clearly...

From what I can gather, the contents of this thread imply to me that Windows does not use Window Scaling? Is this so, could this really be the case? If so then does Windows have limited TCP performance as it can only use a window size of 64Kb?

If Windows does use it, what are they doing differently? Maybe they are just using a small default scaling factor so it doesn't make things horrendous when you have a broken router/web server in your path. Again, this is rather limiting the TCP performance and is just a paper patch over the problem.

Could we set the default scaling factor higher in Windows and then make the call to them? They might listen then :)

If MS ever decide to increase this default, PCF will wish they had listened to all the Linux people phoning in the complaint, helping them debug their faulty systems.

It pisses me off when companies cover up their broken systems with "Sorry, don't support linux". Yeah, let's all use an OS that glosses over the problems so it can bite us in the **** later. Thanks, world.

Tom...

---

### Post by sdowney717 on 2008-11-15
linux is likely more advanced on many types of programming and sites like that are just not up to new networking standards that are supported by linux.  Sort of like windows is the lowest common denominator idea,

---

### Post by tersch17 on 2008-11-21
After experiencing this issue myself, I decided to follow up with PC Financial.  I sent them an email with an explanation of the window scaling problem without even mentioning what OS or browser I was using.  I actually received reply.  Although it was rather generic, it did state that they were aware of the problem and are working to resolve it.  

Anyway - I hope all of you who are experiencing this issue will write or call to PC to hopefully speed up the resolution.  I hate kludgy workarounds!

---

### Post by felipe1982 on 2008-11-27
> **stephanecharette said:**
> 
I've spoken to them several time today to discuss the problem -- I'm hoping that since they've now been told the cause, they'll remove/replace the offending device off their network, or have a fix available soon.

Stéphane Charette

You are awesome! Thanks for sharing knowledge.

---

### Post by uc50_ic4more on 2008-11-27
Since a few of us have received replies from PC Financial stating that they'd be "working on it", would some of those of us out there who have *not* turned off window scaling in /etc/sysctl.conf let the rest of us know here when (if?) the site "goes back to normal"? My biggest concern at this point is that PC Financial will fix their site, but I won't know! :)

---

### Post by kubug on 2008-12-05
Thanks guys, it works now.

---

### Post by djgrant on 2008-12-12
Thanks everyone. I've had the same problem for a while and I'm so glad to have it fixed. I just sent a message off to PC, hopefully if we keep bugging them they will fix it.

---

### Post by Craig73 on 2008-12-16
> **uc50_ic4more said:**
> Since a few of us have received replies from PC Financial stating that they'd be "working on it", would some of those of us out there who have *not* turned off window scaling in /etc/sysctl.conf let the rest of us know here when (if?) the site "goes back to normal"? My biggest concern at this point is that PC Financial will fix their site, but I won't know! :)

It's still an issue.

That being said - realize some companies have a system freeze around year end (if this is even their year end) to minimize risk so we might not see a fix for this until the new year if it's not considered critical.

---

### Post by pbouf on 2008-12-17
YES!! 

['Thank you! ']*100 to the poster who provided the workaround (and such an easy to use one at that). This same problem was preventing me from using remote login to work for the past several weeks, but more recently the PC Financial thing started to bite me as well. I will point their IT support to this thread. Though of course they tend to spout the same 'we don't support Linux' line.

---

### Post by zosky on 2008-12-23
i can confirm they have not fixed thier site yet. 
with intreped paying my bills was a chore.

ive spoken to customer service three times now and the experiences where as noted above; dismisive, unaware and incapable of assisting. the window scaling tip gives instant results !!! WOW !!! thank you.

we need to get this thread and the others infront of the IT crew at PC.financial not a banking telephone agent. any thoughts on how ?

---

### Post by miatared on 2008-12-23
Thank you et Merci Stephane.

Has provided a temp fix and I appreciate it.

Regards,

DS

---

### Post by Leonivek on 2008-12-23
> **zosky said:**
> 
we need to get this thread and the others in front of the IT crew at PC.financial not a banking telephone agent. any thoughts on how ?

Whenever I call any tech support, I ask to speak to a senior technician. It royally pisses me off when a phone agent thinks he knows everything and the caller doesn't because "he works in tech support".  If they ask why or won't forward you, ask them if they know what TCP scaling is, and if they say no, then say, "That's why!".  If you start talking in technical babble, they'll have no choice to send you higher up.  I may even go as far as lie to the telephone agent and tell them you need to speak to a senior technician to report a security problem with the website where it can be compromised and customers' accounts are at risk... or something along those lines.   It may be excessive, but that'll get them moving, hopefully.  Just a thought.

If by mid-January it is still not resolved, I'm definitely calling them and doing just that.  They don't want to listen?  We'll make them listen.

---

### Post by martron88 on 2008-12-23
Thanks for the solution and explanation.  This solved my problem.  I knew that there must be something wrong with pcfinancial.

---

### Post by zosky on 2008-12-24
> **Leonivek said:**
> Whenever I call any tech support, I ask to speak to a senior technician. It royally pisses me off when a phone agent thinks he knows everything and the caller doesn't because "he works in tech support". 


i called again today; told the telephone agent i need to discuss TCP scalling, waited while he got a tech... when he came back, i got " the tech sais you need to talk to your ISP about that"

i escalated and now there is an open ticket with the technical helpdesk, aperretnly this means they will call be back in the next 2 days. 

> **Leonivek said:**
> 
If by mid-January it is still not resolved, I'm definitely calling them and doing just that.  They don't want to listen?  We'll make them listen.

i agree fully !!! **people, we need to be heard**. if you're reading this. call the number on your card. dont settle for vaugue actions and redirections. i was reminded today i've been with them for 8 years. but if an online bank can not manage its IT infostucture properly, i begin to question how strictly they manage to the security of our extremely  sensitive data.

---

### Post by whiteside on 2008-12-28
i can't believe i googled for this and found a whole thread.  thank god, because this has been pissing me off for months, because i think it used to work in linux (like a year ago?).  i called them once and told them it's ******** that they don't support linux, and since they've clearly entered some kind of cartel with microsoft, i'm now forced to go spend $300 on a copy on windows to pay my creditcard with them...

it's a shame, because i, otherwise, really liked this bank.

i'll try the tmp window scaling hax, then call them again later and spout off about it.

---

### Post by rldwallace on 2009-01-03
Thanks to all contributors. Nice to see intelligent life.

I read [http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/) and decided to follow this advice:
> 
Posted Dec 14, 2006 0:15 UTC (Thu) by pcharlan (subscriber, #29128) [Link]
With kernel 2.6.17.13 or higher, you can also do:

THEIR_IP=1.2.3.4
MY_GATEWAY=5.6.7.8

ip route add $THEIR_IP/32 via $MY_GATEWAY window 65535

which only limits window scaling for that destination without interfering with your other connections.

So for me to fix just pcfinancial this was as simple as:

**sudo ip route add 159.231.80.212 via 192.168.0.1 window 65535**

I've only tried a few clicks, but so far, looks good.

Because of the lack of professionalism at PCF, you may find another step I have taken also worth considering:

   From:  David
      To: [email]clientservices@ingdirect.ca[/email]
Subject:  Savings account features
   Date:  Sat, 03 Jan 2009 00:30:17 -0500
 Can I direct deposit my pay as long as my employer offers this service?(Yes)
 Do I get free cheques?(No cheques)
 Can I pay my online bills?(No)
 Can I download transactions in either QIF or OFX formats?(Yes)
 Can I setup regular transfers to an inferior but more physically
 accessible financial institution in order to make cash available?(Yes)
 Thanks,
 David

---

### Post by Leonivek on 2009-01-03
> i escalated and now there is an open ticket with the technical helpdesk, aperretnly this means they will call be back in the next 2 days. So I take it they never called back?

---

### Post by stephanecharette on 2009-01-03
> **Leonivek said:**
> So I take it they never called back?

Maybe 1/2 dozen times I've escalated and been told someone would call back within 48 hours.  I've not once gotten a call back.

I've now written letters to the board of directors which I intend to mail out on Monday.

Stéphane Charette

---

### Post by MGStreak on 2009-01-05
> **rldwallace said:**
> 
So for me to fix just pcfinancial this was as simple as:
**sudo ip route add 159.231.80.212 via 192.168.0.1 window 65535**
I've only tried a few clicks, but so far, looks good.


I tried your solution, and I wasn't able to establish a connection to the website.  (I did replace your IP with mine, just to preempt the obvious question!)
Just so others are aware, if you've tried this method and were unsuccessful, you can easily reverse the changes with the following:
```
sudo ip route del 159.231.80.212
```
If you want to double check that it's gone, you can use:
```
sudo ip route show 159.231.80.212
```
If this command returns nothing, then it's safe to assume the modification is gone.

---

### Post by rldwallace on 2009-01-05
Good to show how to undo changes. Thanks MGStreak.

When you say, 'replace your IP with mine', you do mean your gateway address, correct? In my case, that's the inside IP of the router that I'm connecting to.

It's still working for me...except the entry in the routing table desn't survive a restart. I'm looking into editing the interfaces file as a solution but I don't understand what's going on there. ifconfig tells me I got eth0 but the file only refers to iface for loopback and ppp0. When I try '/etc/init.d/networking restart' I get:
[INDENT]/usr/bin/poff: No pppd is running.  None stopped.
ppp0: ERROR while getting interface flags: No such device[/INDENT]

---

### Post by MGStreak on 2009-01-05
> **rldwallace said:**
> 
When you say, 'replace your IP with mine', you do mean your gateway address, correct? In my case, that's the inside IP of the router that I'm connecting to.

Hmm... I'm using the following to determine my IP address:
1) Right click on network icon in system tray
2) Selecting "Connection Information"
3) IP Address: 192.168.1.101

There is also listed: Broadcast Address, Subnet Mask, Default Route, Primary DNS, and secondary DNS.  Which one is the 'gateway address' you referred to?

As for getting the changes to 'stick'... I'm not really sure how to go about it yet.  If I have success with a different IP address, then I'll look into it.  Any success I have will be recorded in this thread for future reference!

---

### Post by rldwallace on 2009-01-06
> **MGStreak said:**
> Hmm... I'm using the following to determine my IP address:
1) Right click on network icon in system tray
2) Selecting "Connection Information"
3) IP Address: 192.168.1.101

There is also listed: Broadcast Address, Subnet Mask, Default Route, Primary DNS, and secondary DNS.  Which one is the 'gateway address' you referred to?...

Try the address for 'Default Route' for the gateway address.

---

### Post by ceasol on 2009-01-08
I had the same problem here in Edmonton with my SuSE and Ubuntu, but the solution works fine with me I can bank safe from my Linux boxes.

Thanks you guys

---

### Post by kojow7 on 2009-01-10
I just phoned them today, and they told me that no one else has reported any slowness problems in the last number of months, so that the problem must be on my end and most likely a problem with my connection. 

I did not tell them I was using linux (Ubuntu 8.10), because I did not realize it was a linux-specific problem. I had also used a windows machine with a Debian router, and tried my laptop with other peoples' connections, and the same problem existed so I knew it wasn't a problem with my computer or connection. PCFinancial used to work perfectly with linux. The problem is obviously something that they have changed on their end.

So why are they saying that no one else is reporting a slowness problem? Do they just ignore all the calls they get? Do they even record the problems down? Or do they just assume that it is a problem on the clients end and not a problem on their end so figure it is not their problem.

But yeah, I like what someone said, if their tech support staff is not competent enough to realize it is a problem on their end, how can we truly be sure that our information is secure? I mean, hopefully, the tech support do know what they are doing, and it is just the people answering the phone that have no clue. But, even this does not look good for the company. Obviously it would mean that there is no communication between the two departments, which still leads to inefficiency and incompetency. 

If they are going to keep saying that no one else has called about this problem, maybe we ought to schedule a day when we all call them on the same day.

---

### Post by uc50_ic4more on 2009-01-10
> **kojow7 said:**
> If they are going to keep saying that no one else has called about this problem, maybe we ought to schedule a day when we all call them on the same day.

+1

Let's set up a day where we can all call *and* speak to someone "higher up" than the phone operator. Does anyone reading this thread know who we should be asking for, ie. "level 2 tech support" or a "supervisor"? If we can ascertain who it is that *can* listen to us, if not give us some answers, we should all co-ordinate that so that there is some real paperwork on their end for this. I get the feeling that if we call and are dismissed by the phone operators, that there is no record of the call *reaching the right people*.

I'll start: Let's call on Monday, January 19. That way we have a week or so for all of those affected to check back in with this thread, and we're making their Monday all that much worse. :P

Let's also perhaps co-ordinate how we're going to present the issue: Do we mention we're using Ubuntu? Do we tell the "senior tech support folks" what we've come up with as a solution?

---

### Post by allan.w.macdonald on 2009-01-18
Folks,

I have been having a long email conversation with PC Financial over the last few months about this issue.  After several back-and-forths with lower level technical support representatives telling me what kind of browser or OS they supported, blah blah blah, finally, on Nov 14 2008, they made the following statement: "President's Choice Financial is aware of this issue and is currently working with our service providers to resolve it."

I contacted them again on the 9th of December to ask if they knew when the problem would be fixed and on the 12th they replied: "President's Choice Financial is still working with our service providers to address this issue.  I regret that there is currently no timeframe in place for a resolution."

However, the slowness continues to occur.

As you can see, they have acknowledged the problem but it seems that they are not giving it much of a priority.

Maybe if everyone who was having this problem would send an email, explaining the problem, to [email]talktous@preschoicefinancial.com[/email] (if you haven't done so already), they might realize the severity of the issue.

Allan

---

### Post by MGStreak on 2009-01-18
> **allan.w.macdonald said:**
> 
As you can see, they have acknowledged the problem but it seems that they are not giving it much of a priority.

Maybe if everyone who was having this problem would send an email, explaining the problem, to [email]talktous@preschoicefinancial.com[/email] (if you haven't done so already), they might realize the severity of the issue.

E-mail sent.

---

### Post by MGStreak on 2009-01-18
> **rldwallace said:**
> Try the address for 'Default Route' for the gateway address.

I have tried this solution, and it appears to be working!  Thanks for the suggestion!

Regardless, this is an issue President's Choice Financial (or their parent company, CIBC) needs to rectify.  This is not an acceptable workaround for the average user.  As noted earlier, I have sent an e-mail to the PC site... I suggest more people do the same.  The more we talk, the quicker we should be able to mobilize this bug ticket!

As for getting the ip route change command to 'stick,' I have added it to /etc/rc.local so that it is run during bootup.

---

### Post by MGStreak on 2009-01-20
> **MGStreak said:**
> As for getting the ip route change command to 'stick,' I have added it to /etc/rc.local so that it is run during bootup.

Apparently placing this command (ip route...) in my /etc/rc.local has not worked after all... the change does not survive a reboot.  Anyone else have any ideas?

---

### Post by MonctonJohn on 2009-01-20
Thank Dog for that... I would click the link and go surf some other sites until it finished. I'm going to email pcf right now.

---

### Post by CliffD on 2009-01-20
> **MGStreak said:**
> Apparently placing this command (ip route...) in my /etc/rc.local has not worked after all... the change does not survive a reboot.  Anyone else have any ideas?
I'm not sure how to do it in Ubuntu world, but since I'm following this thread, and I just solved your problem on my (vastly superior ;)) Mandriva box, I thought I may as well share. Here's a [link to my blog post]("http://cdugal.pico.ca/2009/01/20/accessing-pc-financial-online-banking-in-linux/"). If it's of use to you guys, feel free to repost relevant info here; otherwise, feel free to ignore it. :D

---

### Post by jvb2k on 2009-01-21
I also have been struggling with this issue for a while - until I thought to search it online :-? - and now it works for me too!! I was also trying to discuss it with PCFinancial, also to no avail. I have just responded to their last email to me, hoping the may get the message, this is what I sent them:

The problem (post #1 and others), root cause (for some insight read posts #33, #41, #42) and the workaround (post #25) - until PCFinancial get their servers fixed - is described in this forum post  [http://ubuntuforums.org/showthread.php?t=959637](http://ubuntuforums.org/showthread.php?t=959637) , or just google search "pcfinancial slow"  . Many other people describe the same issue and many, while attempting to find a resolution, describe fruitless communications with PCFinancial (who are apparently aware of the issue and working to corrected it). I implemented the workaround today and no longer have a problem. I shall continue to follow the forum thread above until the permanent serverside fix is in place and the Linux community become aware of it - hopefully through a notification from PCFinancial.

---

### Post by MGStreak on 2009-01-21
> **CliffD said:**
> Here's a [link to my blog post]("http://cdugal.pico.ca/2009/01/20/accessing-pc-financial-online-banking-in-linux/").
I'm glad you've got a workaround going, but I'm having difficulty implementing it.

I don't seem to have either of these folders:
/etc/sysconfig/network-scripts/ifup.d/pcfinancial
/etc/sysconfig/network-scripts/ifdown.d/pcfinancial

For that matter, I don't even have an /etc/sysconfig/ folder!  Where might these scripts go for a Ubuntu solution?  Furthermore, what should I save the script as?

---

### Post by linux_tech on 2009-01-21
Five minutes and still hasn't loaded. Maybe they need to hire some network Engineers and/or web designers to fix it.

---

### Post by CliffD on 2009-01-22
> **MGStreak said:**
> I don't seem to have either of these folders:
/etc/sysconfig/network-scripts/ifup.d/pcfinancial
/etc/sysconfig/network-scripts/ifdown.d/pcfinancial

For that matter, I don't even have an /etc/sysconfig/ folder!  Where might these scripts go for a Ubuntu solution?  Furthermore, what should I save the script as?

The "pcfinancial" files are simply just executable files with the text I have in my blog (yes, two copies of the same file--not entirely optimised, but it works well enough for my needs). Mandriva's ifup.d and ifdown.d folders work close to /etc/profile.d (whenever there's a new connection/disconnection, all the scripts in the appropriate folder get executed). So, in this way, the correct route can be set up at boot and when I switch between Ethernet and wireless.

I have no clue what the Ubuntu analogue to the above folders is. If it helps, the folders are provided by Mandriva's [initscripts]("http://rpmfind.net//linux/RPM/mandriva/2009.0/x86_64/media/main/updates/initscripts-8.81-8.1mdv2009.0.x86_64.html") package.

A quick google for a Ubuntu ifup.d folder seems to place the folders in /etc/network/ for you. Does this do the trick for you?

---

### Post by MGStreak on 2009-01-26
> **CliffD said:**
> A quick google for a Ubuntu ifup.d folder seems to place the folders in /etc/network/ for you. Does this do the trick for you?

I placed the following code in the a file called pcfinancial in both the ifup.d and ifdown.d folders.  Unfortunately, it appears to not have worked:

```
#!/bin/sh

DEF_ROUTE=$(expr match "$(ip route show to 0.0.0.0/0)" 'default via \([0-9.]*\)')

if [ -n "$DEF_ROUTE" ]
then
    if [ -n "$(ip route show to 159.231.80.212)" ]
    then
        ip route del 159.231.80.212
    fi

    ip route add 159.231.80.212 via "$DEF_ROUTE" window 65535
fi
```

I'm thinking it has something to do with not replacing something in the 'DEF_ROUTE' section with my own ip?  I don't know much about this level of scripting/coding... so any help would be greatly appreciated!

---

### Post by rldwallace on 2009-01-27
I didn't get the init.d thing to work. When I rc'd it, got a message of invalid header. Is there anything special about adding sudo commands in a startup script?

This is what I ended up doing:

Created a text file called PCFix with one line in it:
"sudo ip route add 159.231.80.212 via 192.168.0.1 window 65535"
(The 192.168.0.1 is the internal ip of my router; aka the gateway)

Then in terminal, I cd'd to the folder with PCFix and:
"sudo chmod +x PCFix" and closed terminal.

Then from the File Browser, I just dragged PCFix to the Panel. I was prompted for properties. So I can put my password in when needed, I only changed the type to "Application in Terminal" and said ok. Now I click to fix when required.

---

### Post by Chonnawonga on 2009-02-23
The site seems to be working normally for me now. Maybe they actually fixed it.

---

### Post by Craig73 on 2009-02-24
Agreed... it seems to be working well for me as well.  This must have gone in over the weekend as it wasn't working last week.

A quick sanity check to ensure I didn't have window scaling off...

```

$ cat /proc/sys/net/ipv4/tcp_window_scaling
1

```

(yay)

---

### Post by MGStreak on 2009-02-24
> **Craig73 said:**
> Agreed... it seems to be working well for me as well.  This must have gone in over the weekend as it wasn't working last week. (yay)

I have to agree... it appears to be working for me as well!

---

### Post by brydonhunter on 2009-02-25
I wonder what took them soo long... at least it is working correctly now.

---

### Post by hanzj on 2009-04-26
Do we still need to make changes (e.g.  the line in /etc/sysctl.conf) when we upgrade to Ubuntu version 9.04?

---

### Post by dcstar on 2009-04-26
> **hanzj said:**
> Do we still need to make changes (e.g.  the line in /etc/sysctl.conf) when we upgrade to Ubuntu version 9.04?

My 9.04 works fine on that site (out of the box).

---

### Post by Craig73 on 2009-04-26
> **hanzj said:**
> Do we still need to make changes (e.g.  the line in /etc/sysctl.conf) when we upgrade to Ubuntu version 9.04?

It wasn't a Ubuntu issue but rather a configuration issue with PC Financial which they have addressed.  (So no - not needed in 9.04 or 8.x either)

---

### Post by Craig73 on 2009-04-26
> **brydonhunter said:**
> I wonder what took them soo long... at least it is working correctly now.

We can only assume that, like in most IT environments, that the number of impacted users, who had a work around, didn't justify the risks of rushing in a change, especially near year end, and that it didn't take priority over all their many other issues.  It's all cost/benefit/risk, and most financial institutions err on the side of caution.  

Also, we don't know the structure of their maintenance cycles, assuming this just got flagged to go into a maintenance release rather than emergency fix, then it might only be scheduled into a quarterly release, and if not critical then it wouldn't go into 4th quarter which is year end and preceding RRSP season.  Hard to say really.

---

### Post by Kareeser on 2009-04-26
In any case, I'm glad they got it fixed.

Free chequing and withdrawals FTW!

---

