---
title: "Pidgin yahoo error"
date: 2008-09-20
forum: General Help
---

### Post by lsutiger on 2008-09-20
Recently, I have been getting the following error from Pidgin:```
Unknown error number 0. Logging into the Yahoo! website may fix this.

Pidgin will not attempt to reconnect the account until you correct the error and re-enable the account.
```

It happens about once an hour or so.

Anybody else receiving this error? Or does anybody know what would ecasuig this?

---

### Post by cross157 on 2008-09-21
Bump, I'm getting this say error anyone know what's going on?

---

### Post by Patrick793 on 2008-09-21
I'm getting this too. Must be something with Yahoo's servers or something.

---

### Post by lsutiger on 2008-09-21
I upgraded to 8.04 and it seemed to go away

---

### Post by -Zeus- on 2008-09-21
same error in 8.10

---

### Post by lsutiger on 2008-09-21
Ahhh! It shows  it's face again!!!

---

### Post by lsutiger on 2008-09-22
OK..this needs some attention. Any bug reports made?

I just reported it today to launchpad.

---

### Post by yell0w on 2008-09-23
+1 from me. just random disconnection every few hours.

---

### Post by soro2005 on 2008-09-28
I also get this. Pidgin 2.5.1. My Pidgin also sometimes crashes on checking the Yahoo email account.

---

### Post by carl_schaefer on 2008-09-29
fixed in pidgin 2.5.2, according to this:

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/272952](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/272952)

---

### Post by Mimsy on 2008-09-29
Pidgin has Yahoo issues in Ubuntu, but not under Windows XP. Makes me wonder if it is Pidgin, or if it is something else...? :(

---

### Post by Seb71 on 2008-09-30
I got the same error from Pidgin 2.5.0 in Windows XP in the last 2 weeks or so.

---

### Post by Yfrwlf on 2008-10-01
Yeah everyone should upgrade their Pidgin clients.  Oh wait, you can't because there's no binary to download and no **DEB** package for **Ubuntu** because Linux packaging hasn't been standardized yet, so your only option is to be a geek and compile and screw around with stuff while others laugh at you because they can just click a few times and it's installed.  Yay for us.

Only future Linux feature I care about: help push for at least one standard Linux packaging format.  Kthanx.

---

### Post by loell on 2008-10-01
> **Yfrwlf said:**
> Yeah everyone should upgrade their Pidgin clients.  Oh wait, you can't because there's no binary to download and no **DEB** package for **Ubuntu** because Linux packaging hasn't been standardized yet, so your only option is to be a geek and compile and screw around with stuff while others laugh at you because they can just click a few times and it's installed.  Yay for us.

Only future Linux feature I care about: help push for at least one standard Linux packaging format.  Kthanx.

if you just took a moment to find it, maybe you just could.

[http://www.getdeb.net/app/Pidgin]("http://www.getdeb.net/app/Pidgin")

there are several resons why this could happen,  example the protocol change , and yahoo server issues. because its proprietary we are all guessing till we hit it.

---

### Post by Yfrwlf on 2008-10-01
> **loell said:**
> if you just took a moment to find it, maybe you just could.

I didn't realize I was segregated because of my choice of Linux software to have to go searching elsewhere other than the main developer's website.

If there was at least one standard Linux package, I wouldn't have to.

---

### Post by loell on 2008-10-01
> **Yfrwlf said:**
> I didn't realize I was segregated because of my choice of Linux software to have to go searching elsewhere other than the main developer's website.

If there was at least one standard Linux package, I wouldn't have to.

i don't know why your going off topic. this is a yahoo protocol client issue not linux binary packaging. you can go whine about how about linux packaging in the recurring discussion but certainly not here. as it does not help.

---

### Post by Yfrwlf on 2008-10-01
> **loell said:**
> i don't know why your going off topic. this is a yahoo protocol client issue not linux binary packaging. you can go whine about how about linux packaging in the recurring discussion but certainly not here. as it does not help.

Just responding to you.

Besides, already have the solution, it's to somehow find and update your client to the newest version, so this thread could be closed, really. ^^

---

### Post by loell on 2008-10-01
> **Yfrwlf said:**
> it's to somehow find and update your client to the newest version, so this thread could be closed, really. ^^

the newest version has no yahoo protocol changes so it is not.

---

### Post by Yfrwlf on 2008-10-01
> **carl_schaefer said:**
> fixed in pidgin 2.5.2, according to this:

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/272952](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/272952)

> **loell said:**
> the newest version has no yahoo protocol changes so it is not.

So you're saying they're a liar?  Sad.  Or did you not see that post? ^^

Quote from the page:

[QUOTE=Aaron Haviland]This Yahoo bug is known upstream, and according to the upstream bug report, the fix is fixed in their source, to be released in 2.5.2.

I have not investigated further, but the specific revision is available at:

[http://developer.pidgin.im/viewmtn/revision/info/092bbcea7b768d21baff3362314e784b26b1ced7](http://developer.pidgin.im/viewmtn/revision/info/092bbcea7b768d21baff3362314e784b26b1ced7)
[/QUOTE]

---

### Post by loell on 2008-10-01
> **Yfrwlf said:**
> So you're saying they're a liar?  Sad.  Or did you not see that post? ^^

Quote from the page:

i'm talking about 2.5.1 which the binary package i linked. you are talking about 2.5.**2** **_which is not yet released_**

---

### Post by soro2005 on 2008-10-01
This gets pretty close to what is called trolling!

The problem has been identified, a solution has been committed, and it will soon be available for everybody and for all distributions and flavors. Hopefully, the solution will really solve the issue.

People who prefer the bug fixing and release cycles of commercial software products know where to turn to.

People who don't like GetDeb and want to stay up to date can add the Pidgin PPA to their sources.list:

[https://launchpad.net/~pidgin-developers/+archive](https://launchpad.net/~pidgin-developers/+archive)

---

### Post by Yfrwlf on 2008-10-01
> **soro2005 said:**
> This gets pretty close to what is called trolling!

If that was directed at me, complaining about a lack of installable Linux packages on the developer's website is not trolling.  Trolling is trying to be mean and provocative, and I wasn't doing either. ^^

---

### Post by loell on 2008-10-01
you're diluting the topic by inserting your linux packaging grudges, this isn't the right thread for that, so just stop it.


to churn the topic on the right track, here are the issues

1. Just ping yahoo server every 60 minutes.
2. do a keepalive every  minute.

---

### Post by lsutiger on 2008-10-04
Thanx soro2005!
I updated to the latest, let's see what happens.

---

### Post by omega13a on 2008-10-04
> **loell said:**
> 
to churn the topic on the right track, here are the issues

1. Just ping yahoo server every 60 minutes.
2. do a keepalive every  minute.

Sorry if I sound dumb (I didn't get much sleep last night) but how do you do that?

---

### Post by loell on 2008-10-04
> **omega13a said:**
> Sorry if I sound dumb (I didn't get much sleep last night) but how do you do that?

you don't, its the client's job(ie pidgin). as this thread points out it's supposedly fixed in version 2.5.2 which  atm is not yet available.

---

### Post by lsutiger on 2008-10-04
I added the repository in soro2005's post and upgraded to 2.5.1 earlier and it hasn't dropped yet.
So any of you not running that version might want to try that solution.

---

### Post by siddartha on 2008-10-12
The solution is the same dating some looong years ago - dump pidgin, gaim, or whatever they want to call it in hope people will lose track with their interminable list of bugs. Really, this is one of the worst "main" pack with issues being ported over major versions as change of version doesn't mean solving problems, more like doing a change of interface.

The list of issues is long, the approach is wrong and in the end some good souls like the Trillian guys help them out. After numerous bugs and features requests deleted "because it is in the cvs" (and it wasn't) and "because we're moving the servers" I decided this team does not need help and the users are handled like a commodity to gain something like a warm seat at Google. Because of that a team involved into getting the audio and video support worked for nothing as the lead developer changed all to make room for Google Talk - this way there is no multimedia support, but he has a nice blog with his face all over.

---

### Post by Yfrwlf on 2008-10-13
> **siddartha said:**
> The list of issues is long, the approach is wrong and in the end some good souls like the Trillian guys help them out. After numerous bugs and features requests deleted "because it is in the cvs" (and it wasn't) and "because we're moving the servers" I decided this team does not need help and the users are handled like a commodity to gain something like a warm seat at Google. Because of that a team involved into getting the audio and video support worked for nothing as the lead developer changed all to make room for Google Talk - this way there is no multimedia support, but he has a nice blog with his face all over.

Jabber now has Jingle for video/audio communications, so Gaim really can't ignore adoption any longer just because "GTalk" (Jabber) doesn't have it, because I'm sure GTalk will get it at some point in the not too distant future now, if that really was the reason why Gaim has neglected it's adoption.  All I know is the one dev told me he wasn't interested, so if you want to webcam or whatnot as well as chat, you should try other programs like Kopete and such, or even use Skype if you don't mind being even more proprietary (since Kopete supports Jabber, which of course is completely open, and also the Skype client isn't open).

Any way, I hope Gaim will improve, but Linux users should definitely check out some of the other IM clients out there. ^^

---

### Post by lsutiger on 2008-10-13
I d/l and installed kopete from the repositories, but I can't get my gtalk account to log on (through jabber). Is there a different way to set up kopete vs pidgin?

Found it here:
[http://techwithfun.blogspot.com/2007/11/configuring-kopete-for-google-talk.html](http://techwithfun.blogspot.com/2007/11/configuring-kopete-for-google-talk.html)

---

### Post by Mimsy on 2008-10-13
Wow, that was only two pages I had to dig through before I found a post that gave me a solution. Could you please talk open source politics someplace other than in this thread? 

Just add that repository and update, was it?

---

### Post by lsutiger on 2008-10-13
Well, I have been playing with Kopete for a day now and I do not like it. I can not ,message anybody who is not on my list. I do not care about vid-chat, but the bug where I get kicked every hour or so really is inconvenient. None of the other clients I have installed in the past has been satisfying.

Anybody hae any other ideas?

---

### Post by Mimsy on 2008-10-15
> **lsutiger said:**
> Anybody hae any other ideas?


Well, if I was cynical I would tell you to go back to Windows, where IM clients actually work, but that would be a low blow, now wouldn't it? ;)

---

### Post by dahlheim on 2008-10-16
sudo apt-get remove pidgin
sudo apt-get remove libpurple0

then download the new version for your architecture (32 vs 64-bit) from [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

and install (first pidgin-data, the libpurple0, then the application .deb files)

worked for me.

---

