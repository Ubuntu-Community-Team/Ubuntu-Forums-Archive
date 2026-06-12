---
title: "Evolution: unable to send email through SMTP"
date: 2008-10-04
forum: General Help
---

### Post by woodeast on 2008-10-04
Hello, 

I'm using Hotmail Plus, with the following configuration on Evolution:
> 
Incoming (POP): pop3.live.com
Outgoing (SMTP): smtp.live.com

Retrieval of mail works fine, but sending does not:

> Error while performing operation.

Could not connect to smtp.live.com: Connection timed out 

Any suggestions as to how I can send through SMTP?

Thanks!

---

### Post by PocketDog on 2008-10-05
Does this help? [http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

---

### Post by tonybaqain on 2008-10-05
1: to check if the port is open from live.com side use this: 
```

nc -z -v smtp.live.com 25

```

if it gives you **smtp.live.com [xxx.xxx.xxx.xxx] 25 (smtp) open**, then you must recheck your evo configuration, like smtp authentication and/or using ssl or not.

if it gives you any other messages, then try this :
```

sudo iptables -F
nc -z -v smtp.live.com 25

```

if the same error message appears, then it appears to be a middle-way problem between you and live.com smtp server on port 25. 

if the message appearing has an **open** word, then it is your local firewall / iptables are banning the connection, **iptables -F** would do the work for you, also if you have a router / wireless router, check its firewall rules also.

have fun :)

---

### Post by woodeast on 2008-10-05
@ PocketDog: Thanks, but I'm trying to send through smtp.live.com, instead of setting up my own smtp server. 

The problem seems to be that smtp.live.com isn't detected by evolution? Perhaps my ISP block access to external smtp servers?

@tonybaqain: trying out your solution. netcat isn't giving me an output at all (with or without using iptables). What is that suppose to mean? Thanks!

edit: after about 5 minutes... netcat gives me:

> smtp.live.com [65.55.172.254] 25 (smtp) : Connection timed out


---

### Post by tonybaqain on 2008-10-05
it seems like what you said, a middle-way machine is banning the connection from your side to smtp.live.com, anyway, why don't you use your isp's smtp server ?

if my isp is orange.com , ill try nc -z -v smtp.orange.com 25 or mail.orange.com 25 , it will allow me to connect to the smtp using it.

---

### Post by woodeast on 2008-10-05
I can actually send emails using my own smtp server on my domain name, from the hotmail account. 

But the thing is, hotmail checks the senderid, and if the email is a @hotmail.com address and sent from a different server, it marks it as a "potentially dangerous" email when you view it from webmail.

Is there a way to send from a server other than hotmail's own and not get marked as a phished email? Thanks.

---

### Post by tonybaqain on 2008-10-05
actually, 

from my expirience , no one allows you to send emails through their own services, unless they provide you with such things.

i have a maktoob.com account, but i send mails through my isp's smtp server.

---

### Post by woodeast on 2008-10-05
Yeah... I do have my own smtp server under that's a part of my hosting plan. It's just that hotmail thinks that it's a phished email (coming from a non hotmail server using hotmail.com address) when I send from my own server.

---

### Post by meperry64 on 2009-02-10
Using Evolution to send/receive Live mail, my solution:

Server: smtp.live.com
Use Secure Connection: TLS Encryption
Authentication Type: Login

Mp

---

### Post by Knacker on 2009-02-26
this suddenly became a problem for me a few days ago. 

i think M$ is messing around with ports...there's mention of this happening on a number of different forums. sending mail worked fine until a couple of days ago. had to switch port to 587 (i.e. smtp.live.com:587). this fixed everything immediately. 
why do I keep using hotmail!?

---

### Post by dodd_alex on 2009-03-06
I have suddenly hit this wall as well. I was sending and receiving through hotmail using evolution, and receiving through gmail as well, all flawlessly for the last couple of months. I have had to start with a fresh evolution due to unrelated reasons and now suddenly I can only receive from both with no sending through either, no matter how many of the setting combinations I change. What gives?

---

### Post by dodd_alex on 2009-03-06
I just went to my gmail account, followed these instructions:

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html)

and now everything in that account is working perfectly. still haven't figured out the hotmail yet though...

---

### Post by cantillon on 2009-03-07
Meperry64's solution + Knacker's solution worked for me:

Server: smtp.live.com:587
The server requires athentication: Yes
Use secure connection: TLS Encryption
Authentication type: login

Thank you both...

---

### Post by ryanrich on 2009-05-04
> **meperry64 said:**
> Using Evolution to send/receive Live mail, my solution:

Server: smtp.live.com
Use Secure Connection: TLS Encryption
Authentication Type: Login

Mp

Thanks for this tip, it worked for me, and have been struggling with this all week! Big thumbs up to you!

---

### Post by irvotheturbo on 2009-06-01
> **cantillon said:**
> Meperry64's solution + Knacker's solution worked for me:

Server: smtp.live.com:587
The server requires athentication: Yes
Use secure connection: TLS Encryption
Authentication type: login

Thank you both...

I had the TLS set correctly, but the port number fixed it eventually. Thanks!
:popcorn:

---

### Post by andersonluk on 2009-06-13
> **cantillon said:**
> Meperry64's solution + Knacker's solution worked for me:

Server: smtp.live.com:587
The server requires athentication: Yes
Use secure connection: TLS Encryption
Authentication type: login

Thank you both...

  That finally works for me after many days of searching

---

### Post by gvsopic on 2009-08-25
When I changed the encryption type to TLS, it all worked, not with the other two types.

---

### Post by DrDunkMcNally on 2009-10-08
Hi there, 

Just started using evolution mail and I'm having the same problem where I cannot send emails through SMTP, this is the error I get:

"Error while performing operation.

RCPT TO <emailaddress@here.xx> 
failed: Administrative prohibition"

My mail client is startlogic.com, I have to use port 587 (at least in my outlook that's what I was using, and everything works perfectly there.)

My outgoing mail works fine, and has been since I started using evolution.

I'm also new to Ubuntu, is this something I need to fix on my own system?  or a setting I need to fix in evolution mail?

Any help is greatly appreciated, if you need more information please don't hesitate to let me know.

-Cheers

---

### Post by KapteinPyn on 2009-11-01
> **cantillon said:**
> Meperry64's solution + Knacker's solution worked for me:

Server: smtp.live.com:587
The server requires athentication: Yes
Use secure connection: TLS Encryption
Authentication type: login

Thank you both...

Thanks worked for me!

---

### Post by z-itou16 on 2009-11-03
DrDunkMcNally,

check if your smtp mail server needs any kind of security method and authentication. you can use this command to check if you have open port to your smtp server  nc -z -v smtpserver port (replace smtpserver for your actual smtpserver and port for your actual listening smtpserver port)

good luck

---

### Post by DrDunkMcNally on 2009-11-04
> **z-itou16 said:**
> DrDunkMcNally,

check if your smtp mail server needs any kind of security method and authentication. you can use this command to check if you have open port to your smtp server  nc -z -v smtpserver port (replace smtpserver for your actual smtpserver and port for your actual listening smtpserver port)

good luck

I have checked all of these things.  It does not require security however it does need authentication, I have selected require authentication -> Plain ->username...

I truly do appreciate the help, and while the issue I was having is not solved it is now a non-issue.  I've installed Ubuntu on a different laptop and am using Evolution without any hitches.  I am unsure if the problem arose becuase I had vista running Outlook installed on the other partition of my hard drive at the time, but I no longer do (I do however have outlook on one laptop for work, and evolution on my home laptop for personal use)

Anyway the settings required a new port for smtp and all that fancy jazz, I had every setting identical to the way I have them now, it just refused to work, it's quite possible it was simply a glitch in the setup or something.  Anywho, it's over now, I'll mark the topic as solved, but it isn't really.

Thanks again for the help!
DUNK

So I WON'T mark the topic as solved because it isn't mine!! :P  Sorry fellas and ladies!

---

### Post by DavidPitt on 2009-11-11
meperry64 has it on the nose. Those settings worked perfectly for me, maybe some netcat tests helped jog it too...

---

### Post by mbr78 on 2009-11-11
I wasn't able to send Hotmail through smtp.live.com in Evolution either. I got it working by changing SSL encryption to TLS encryption under 'Security' on the 'Sending Email' tab in the 'Account Editor'.

---

### Post by AtrocityDT on 2010-02-07
This thread was very helpful. My problem however was fixed by realizing I had mispelled smtp haha. I had it listed as smpt and through typoglycemia I did't even notice!

---

### Post by mi.kmaq on 2010-02-15
thanks

> **meperry64 said:**
> using evolution to send/receive live mail, my solution:

Server: Smtp.live.com
use secure connection: Tls encryption
authentication type: Login

mp

---

### Post by allgood416 on 2010-02-22
for me it was different. 

under ubuntu 6.06

smtp.live.com:587
TLS
Login

when you send/recieve, you will be prompted to input your hotmail password.

:popcorn:

p.s after all these years of using ubuntu, ive never registered to this website. i felt that this was a important enough reason to input my opinion. hope it helps

---

### Post by VitaLiNux on 2010-03-12
> **meperry64 said:**
> Using Evolution to send/receive Live mail, my solution:

Server: smtp.live.com
Use Secure Connection: TLS Encryption
Authentication Type: Login

Mp

Thank you! Now I can send messages successfully! :KS:KS:KS:KS:KS

---

### Post by tersogar on 2010-03-16
I almost give up on Evolution but thanks to all of you the problem was solve. I suspect that is what Ubuntu mean, humanity for all.  

Thanks :KS:KS:KS:KS:KS

---

### Post by Taiyou on 2010-05-02
> **cantillon said:**
> Meperry64's solution + Knacker's solution worked for me:

Server: smtp.live.com:587
The server requires athentication: Yes
Use secure connection: TLS Encryption
Authentication type: login

Thank you both...

This also did the trick for me, thanks a lot!

---

### Post by itsageo on 2010-05-16
Just perusing this thread to get some help with my hotmail account and the changing to TLS and port 587 worked great for me.  However, I still had trouble with my college email working through evolution... so I remembered what I did in thunderbird.

Although not ideal, you can send many email accounts through the gmail server.  Just put in the same stuff into the "sending" fields and wit will work just fine.

---

### Post by barna10 on 2010-07-20
> **cantillon said:**
> Meperry64's solution + Knacker's solution worked for me:

Server: smtp.live.com:587
The server requires athentication: Yes
Use secure connection: TLS Encryption
Authentication type: login

Thank you both...

This worked great for me. Only difference is I'm using PLAIN authentication.

---

### Post by elambert85 on 2011-04-22
> **Knacker said:**
> this suddenly became a problem for me a few days ago. 

i think M$ is messing around with ports...there's mention of this happening on a number of different forums. sending mail worked fine until a couple of days ago. had to switch port to 587 (i.e. smtp.live.com:587). this fixed everything immediately. 
why do I keep using hotmail!?

This worked like a charm for me.

---

### Post by popeyeray on 2011-06-01
> **barna10 said:**
> This worked great for me. Only difference is I'm using PLAIN authentication.

I like simple solutions like yours, no extraneous reasons to hear oneself speak of their knowledge, and give self accolades. 
Thank you, this worked perfectly.

---

### Post by Smallwheels on 2011-06-24
> **cantillon said:**
> Meperry64's solution + Knacker's solution worked for me:

Server: smtp.live.com:587
The server requires athentication: Yes
Use secure connection: TLS Encryption
Authentication type: login

Thank you both...

This didn't work for me with Ubuntu 10.04 LTS

Now since I've removed and reinstalled Evolution, it isn't receiving messages either.

---

### Post by Smallwheels on 2011-06-24
I also checked the 587 port using the terminal and the information above. The result was:
 succeeded!

So I know that port 587 is open. 
The thing is the error message I get is telling me the authentication method is POP Before SMTP AUTH USING A NON-POP SOURCE.

I have the authentication set to PLAIN and before that it was Login. Neither works. 

I started a different thread about this. Anybody wanting to take a stab at fixing this let me know here or at the other thread that is newer. It lists the things I've tried.

[http://ubuntuforums.org/showthread.php?p=10977470#post10977470](http://ubuntuforums.org/showthread.php?p=10977470#post10977470)

---

