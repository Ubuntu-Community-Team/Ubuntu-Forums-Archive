---
title: "College blocks linux! How can I get around it?"
date: 2008-09-21
forum: General Help
---

### Post by J-E-N-O-V-A on 2008-09-21
They've managed to get some way of blocking my internet access because I'm using ubuntu. At least I think they have. Everybody that has windows or mac can access the network instantly whereas I have to put in bssids, tkip passwords etc that I don't think anybody knows except the tech guys. 

So, is there any way to get around this?

---

### Post by lukjad on 2008-09-21
I think the reason that you don't have internet access is because you are on a network. If you wish to get to the 'net you need the proxy number and the port number. Go to a fellow college computer user and open Internet Explorer. Go to Tools->Internet Options->Connections->LAN Settings.

Copy the info you see there then go to your PC and open Firefox and go to Edit->Preferences->Advanced->Network->Connection and click on Settings. The select Manual Proxy Configuration and enter the HTTP Proxy and the Port number. 

This will enable Firefox to browse the web. To get Synaptic to access the web Go to System->Preferences->Network Proxy and select manual proxy settings. Re-enter the HTTP proxy and Prot and all should work.

---

### Post by mb_webguy on 2008-09-21
They probably have some sort of automatic configuration script for Windows and Mac users.

If the information about how to connect to the network works, then go with it.  It's probably the same configuration the Windows and Mac users are using, it's just that you're having to set it up manually.

---

### Post by J-E-N-O-V-A on 2008-09-21
> **lukjad007 said:**
> I think the reason that you don't have internet access is because you are on a network. If you wish to get to the 'net you need the proxy number and the port number. Go to a fellow college computer user and open Internet Explorer. Go to Tools->Internet Options->Connections->LAN Settings.

Copy the info you see there then go to your PC and open Firefox and go to Edit->Preferences->Advanced->Network->Connection and click on Settings. The select Manual Proxy Configuration and enter the HTTP Proxy and the Port number. 

This will enable Firefox to browse the web. To get Synaptic to access the web Go to System->Preferences->Network Proxy and select manual proxy settings. Re-enter the HTTP proxy and Prot and all should work.

Yeah I've tried all that. Also they've managed to make firefox very very very slow, so that you have to enter username and password everytime an image is uploaded on a page.

Oh well, I'm learning backtrack 3 now. If it doesn't let me on tomorrow I'll just kill the network in a few weeks...

:)

---

### Post by lukjad on 2008-09-21
Have you tried asking the techs who work there for the passwords? Alternately, try to install Ubuntu over XP and then import the XP settings. That may be enough to get the needed paswords or whatever it is.

---

### Post by lisati on 2008-09-21
+1 for the ideas suggested so far.... and don't forget to be nice to the tech guys. You don't want your education to be ruined by an unwarranted reputation for the "wrong" kind of hacking, even if you do pull a prank or two.

---

### Post by lukjad on 2008-09-21
Also, you could try and use an encrypted proxy (if you are allowed). This may speed things up a tad.

---

### Post by AceDip on 2008-09-21
Well i cant really imagine how can anyone(especially an educational institution) block or restrict the use of comp os.
Its a bloody clear violation of rights of anybody to not to allow him to use his "personal computer", the way he wants.
I guess people still do not get the meaning of the term PC.

---

### Post by The Cog on 2008-09-21
Two thoughts:

Firstly, there is a firefox extension "User Agent Switcher" that allows you to get firefox to announce itself as IE.

Second, if they are using a Microsoft ISA as a firewall then you will have to be joined into the Windows domain before it lets you through unimpeded. You may need to look at samba to see how to join the domain.

---

### Post by Therion on 2008-09-21
> **AceDip said:**
> ... Its a bloody clear violation of rights of anybody to not to allow him to use his "personal computer", the way he wants.
I guess people still do not get the meaning of the term PC.
Really?  Remind me again who's property he's on at the time and who's network he wants to use?  

I assume you're fine with me, or anyone else for that matter, using YOUR network then, any way I/they choose?

---

### Post by ThrobbingBrain66 on 2008-09-21
> **Therion said:**
> Really?  Remind me again who's property he's on at the time and who's network he wants to use?  

I assume you're fine with me, or anyone else for that matter, using YOUR network then, any way I/they choose?

That's rubbish.  The network is made available for the students to use for school work, entertainment and whatever else they (legally) want to use it for.  The OS that a student uses should be of little concern to the school.

/rant

Back on topic.  You really should talk to the school's tech support to see what the problem is and what they can do to help you.  School networks should be OS agnostic.

---

### Post by lukjad on 2008-09-21
While I agree in theory, there *may* be a good reason. Perhaps there is a policy there to help students out with computer woes. If that is so, then maybe they just do not have any Linux certified staff. Also, if certain programs need to be installed on the student's computer, Linux may not be a supported platform. I do not agree, but it is their network and their rules. If they are there you have the right to fight it, but they have the right to deny you that right. If a campus denied people the right to use Windows on the network because they didn't want the network to be breached, that would be their right. 

That being said, I don't think that it is very nice of them.

---

### Post by lswb on 2008-09-21
> **J-E-N-O-V-A said:**
> They've managed to get some way of blocking my internet access because I'm using ubuntu. At least I think they have. Everybody that has windows or mac can access the network instantly whereas I have to put in bssids, tkip passwords etc that I don't think anybody knows except the tech guys. 

So, is there any way to get around this?

It's unlikely they are blocking your access simply because you use linux. Probably just a matter of getting the settings correct for their network and saving them. Is this wired or wirless? If wireless, do you know what kind of protection is used? WEP, WPA, none? and if so, what the passkeys are?

---

### Post by Therion on 2008-09-22
> **ThrobbingBrain66 said:**
> The OS that a student uses **should** be of little concern to the school. ... You really **should **talk to the school's tech support...  School networks **should** be OS agnostic.
The way it *should* be is frequently not the way it *is*.  Not that I'm not sympathetic.

> **lukjad007 said:**
> ... but it is their network and their rules. If they are there you have the right to fight it, but they have the right to deny you that right. 
They'll tell you it's not a "right" it's a privilege.  It is their network and it's theirs to administer as they see fit.  Then they'll tell you about uniformity and support and so on.  Bitch all you want, that's the way it is.  Agreeing to all of their rules regarding using their network is probably buried somewhere in all that paperwork you filled out when you registered.  I know because I've worked on a college campus for the last eight years.

---

### Post by mb_webguy on 2008-09-22
While I agree with ThrobbingBrain66 that universities *should* be platform agnostic, personal experience says leads me to agree with Therion that things too often aren't the way they should be, especially in the political world of academia.  Also logic tells me that they have no obligation to be so, since even if funded by the state, a university is a business, and caters to the needs of the common student.  The vast majority of tuition revenue comes from Windows users, so that's where they will naturally provide the most support.  A small (but growing) minority of students are likely to run Linux, so university IT services naturally won't provide (and often don't see any point in providing) much support for Linux.  On top of that, many universities now have partnerships with Microsoft to sell Microsoft products to students at a discounted price, and therefore actually have an economic incentive to not support Mac and Linux.

However, let's step away from that for a moment, because I just had an idea that might actually prove *useful* to the OP, and I don't know why I haven't thought of it before now.

Rather than going to the university help desk for support, go to the university's computer science department!  CS students and faculty, in my experience, tend to know more about computers in general than the people hired by the university's computer services department, but you're also likely find quite a few people who use Linux themselves.  Check to see if there's a computer science club, and if so, contact them for help.  If there isn't a computer science club, just ask around the CS department for someone who knows about Linux.  I'm sure you'll be able to find a few.

---

### Post by ugm6hr on 2008-09-22
> **J-E-N-O-V-A said:**
> Yeah I've tried all that. Also they've managed to make firefox very very very slow, so that you have to enter username and password everytime an image is uploaded on a page.

Does this mean you can connect, albeit slowly with Ubuntu / Firefox?

I think you need to give a bit more information about how Windows (or perhaps more useful - Mac users) connect to the network (i.e. personal username etc).

Also - what exactly happens when you try to connect with Ubuntu.

I have actually found that it is easier to use Linux on wired university / work networks to get online than Windows (as long as you have a legitimate username / password).

---

