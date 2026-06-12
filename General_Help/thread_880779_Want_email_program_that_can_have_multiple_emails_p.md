---
title: "Want email program that can have multiple emails pushed to it &amp; work in XP &amp; ubuntu"
date: 2008-08-05
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-05
Alright, I dont even know if this is possible, but I would love it if it was.

I'm looking for one program that will be able to be used seamlessly between Ubuntu and windows for email.

Now there are a couple of stipulations...

1) I want it to be able to have several emails pushed to one central location (this program) so I dont have to continually check 4 or 5 emails boxes.

2) I also want it to be as seamless as possible regardless of what OS I will be in.

3) If I delete an email in Ubuntu, I want it to also delete it when I go in windows so I dont have to do double the work.

4) I would like some type of program that runs in the background so I dont actually have to have the application fully open persay, but will somehow notify me that new mail has arrived...

Sort of like AOL's "you've got mail" or the way MAX OS seems to have those little icons change based on receiving new mail.

Am I making any sense?

Is this at all possible?

---

### Post by Mgiacchetti on 2008-08-05
get a yahoo account.

forward all email to that account.

---

### Post by LowSky on 2008-08-05
well you could set up your own mail server. It can download all your messages to one central location and you can have any client (like thunderbird) veiw the mail
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

---

### Post by PsychedelicWonders on 2008-08-05
lowsky, so what youre talking about, it will allow me to do all of these things I want?

Both in Ubuntu and Windows?

That link is a complete walk through to setting this email system up?

I havent read it yet... in the process of doing so now.

---

### Post by Mgiacchetti on 2008-08-05
ok the only way of being able to have deleted mail in windows be deleted in ubuntu at the same time, is to use an online mail application, (like yahoo for instance)  thats why I was saying to do it that way.  

It will prevent headaches and years of frustration.

---

### Post by Mgiacchetti on 2008-08-05
UNLESS you use IMAP for all of your email accunts.

---

### Post by PsychedelicWonders on 2008-08-05
I'd prefer to be able to have some type of application run in the background and notify me via some type of icon that changes like MAC OS does.

I'd really want to stay away from yahoo and having to keep logging back in to check for updates.

What is this IMAP you speak of?

---

### Post by Mgiacchetti on 2008-08-05
[SIZE=-1]Internet Message Access Protocol. A protocol for accessing electronic e-mail (or bulletin boards). IMAP allows e-mails to be read by a client but still be stored on a central server. IMAP is suited to environments where people need to be able to access their e-mail from more than onw workstation.[/SIZE]

---

### Post by hyper_ch on 2008-08-05
with thunderbird you can share the profile folder between xp and linux. So if you have pop3 only accs then that is the way to go.

---

### Post by PsychedelicWonders on 2008-08-05
So does this IMAP run smoothly in both Ubuntu and xp?

is this some type of application that runs in the background and notifies me via an icon?

Can I add any addtional code into anything for this icon thing to work?

If it makes any difference with this icon situation I want, I will be modifying my Ubuntu to look like the MAC OS.

But then how can I get this same icon in windows?

---

### Post by Mgiacchetti on 2008-08-05
this IMAP is an option in (i would think) any mail program so if you have thunderbird, outlook, etc you should be able to change your settings and go.

---

### Post by PsychedelicWonders on 2008-08-05
> **hyper_ch said:**
> with thunderbird you can share the profile folder between xp and linux. So if you have pop3 only accs then that is the way to go.

What determines whether I have only pop3 or not?

---

### Post by hyper_ch on 2008-08-05
your provider which gives you the email accounts. There you should also have the option of forwarding all incoming email to another email account.

---

### Post by PsychedelicWonders on 2008-08-05
> **Mgiacchetti said:**
> this IMAP is an option in (i would think) any mail program so if you have thunderbird, outlook, etc you should be able to change your settings and go.

Well I will use both mozzilla and thunderbird on both OS to keep myself as familar with them as possible.

So I use this IMAP in conjunction with thunderbird?

---

### Post by hyper_ch on 2008-08-05
with IMAP you can use any email client that supports it. The email will be left on the server and it will sync your local folder with the data. However some email providers will delete the email after a given period of time. In that case IMAP might not be suitable for you.

If you have only POP3 access then you download the email and it's not on the server anymore. In that case you would need a way to use the same profiles on linux and windows. With thunderbird you can do that.

---

### Post by PsychedelicWonders on 2008-08-05
Alright, so where is there a step by step walk through of getting this IMAP/thunderbird process going?

I assume from everyones talks, that thunderbird is unbuntu/mozzillas form of outlook?

Can i set notification icons on the desktop with either a visual or a sound?

---

### Post by lordadi on 2008-08-05
Hi,

You can use thunderbird in both Ubuntu and XP and share a profile between them.This is an excellent page:[MozillaZine]("http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux") and also [Share thunderbird profile]("http://learn.clemsonlinux.org/wiki/Email:Sharing_your_Thunderbird_profile")


Cheers,


Lordadi.

---

### Post by loboc on 2008-08-05
Steps

1 Set up Gmail Account

2 Configure Gmail accoun to retrieve your current POP3 mail
[http://googlesystem.blogspot.com/2006/12/screenshots-of-gmails-mail-fetcher.html](http://googlesystem.blogspot.com/2006/12/screenshots-of-gmails-mail-fetcher.html)

3 Install Thunderbird everywhere

4 Configure Thunderbird to Retrieve IMAP mail from gmail
[http://mail.google.com/support/bin/answer.py?hl=en&answer=75725](http://mail.google.com/support/bin/answer.py?hl=en&answer=75725)

5 Thunderbird can be configure to alert you to messages when its running using popups

---

### Post by PsychedelicWonders on 2008-08-05
So I'm setting up a gmail account to have all of my other accounts forwarded to?

Then I just have thunderbird continually check the gmail account?

Is this still considered setting up my own mail server?

I may just buy a domain name and set up an entirely new mail server that way.

I think it will be alot easier than trying to track down all of these other accounts.

If I set up a domain and use that as my new email, would I be able to check it from anywhere like i can in hotmail lets say?

---

### Post by LowSky on 2008-08-05
it wont be like hotmail. you will not be able to use say firefox to open a webpage to view email easily. You could use a laptop that has access to your own mail server with something like Thunderbird and view them that way while on the go, but from any computer terminal including a strangers thats not easily done, unless you set up a web viewable client an example whould be this [http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

---

### Post by PsychedelicWonders on 2008-08-05
well if i use my home HTPC as my server,  and have say an iPhone, then would I be able to check my mail anywhere I may be at that time if my iPhone is somehow connected to my home HTPC/server?

I would eventually like to hook up a laptop perhaps as well, so I would assume the same protocol would be used to get it on the network of my htpc/server like the iPhone?

---

### Post by PsychedelicWonders on 2008-08-05
> **LowSky said:**
> it wont be like hotmail. you will not be able to use say firefox to open a webpage to view email easily. You could use a laptop that has access to your own mail server with something like Thunderbird and view them that way while on the go, but from any computer terminal including a strangers thats not easily done, unless you set up a web viewable client an example whould be this [http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

This sounds intriquing...

bulletin boards, instant messaging - Are these message boards that I am already a part of and somehow it just "hosts" like a mini hot button to quickly take me there?  Same with instant messages?  Can I use my own IM system (ICQ) or whatever I may choose to use in this program so I have a large database of people, or do I have to start a new account and username with this programs own instant messainger?
Am I understanding this right?


allowing unlimited horizontal scalability - What exactly does that mean?

---

### Post by AndyCooll on 2008-08-05
If you have a Gmail account, you have a web-based email account. You can also configure this account to view other email accounts from other service providers (provided the other service providers allow this). The minimum you need for all this is a web-browser.

Also/alternatively you could setup your pc based email application (e.g. Thunderbird, Evolution etc) to collect your emails using IMAP. This works by synchronising your emails on your pc with the emails on the email server, but crucially leaving the original email on the server. So if you then went to another pc and setup another email client to view your emails, since they're still on the server it can also synchronise and view those same emails.

Neither of these are a home email server, that's a whole topic in itself.

I used to use IMAP, but these days I simply use Gmail in it's web-based version. Less hassle.

:cool:

---

### Post by PsychedelicWonders on 2008-08-05
> **AndyCooll said:**
> If you have a Gmail account, you have a web-based email account. You can also configure this account to view other email accounts from other service providers (provided the other service providers allow this). The minimum you need for all this is a web-browser.

> Also/alternatively you could setup your pc based email application (e.g. Thunderbird, Evolution etc) to collect your emails using IMAP. This works by synchronising your emails on your pc with the emails on the email server, but crucially leaving the original email on the server. So if you then went to another pc and setup another email client to view your emails, since they're still on the server it can also synchronise and view those same emails.

I like this idea because I can use icons to notify me at least while I am at home of when I have mail instead of having to contintually check it every 2 minutes.

Will this "icon notification" I'm speaking of also be able to be put on an iPhone?

But when do you say it crucially leaves the original on the server...

Is that a good thing or a bad thing?

When I delete it in thunderbird in Ubuntu, I dont want to have to re-delete it in thunderbird in windows, I want it deleted forever the first time regardless what OS or machine(home HTPC, laptop or iPhone) I am on. 

Will thunderbird work on an iPhone does anyone know?

> Neither of these are a home email server, that's a whole topic in itself.

What exactly is this?  Is this where I register a domain name and use that as my email and use my home computer as the server?

---

### Post by PsychedelicWonders on 2008-08-06
bump

---

### Post by PsychedelicWonders on 2008-08-07
anyone know of have a walk through to do what I'm trying to do with thunderbird and IMAP?

---

### Post by jimv on 2008-08-07
> Will this "icon notification" I'm speaking of also be able to be put on an iPhone?

Yeah, the iPhone supports IMAP email servers.

> But when do you say it crucially leaves the original on the server...

Is that a good thing or a bad thing?

That's a good thing.  When you use a POP email server, you download your messages onto one machine and then that's the only place they exist.  With an IMAP server, it keeps the messages on the server and puts a copy on your machine so you can still get your message from any other machine that you have set to use that account.

> When I delete it in thunderbird in Ubuntu, I dont want to have to re-delete it in thunderbird in windows, I want it deleted forever the first time regardless what OS or machine(home HTPC, laptop or iPhone) I am on.

Thats the whole idea behind an IMAP server.

> Will thunderbird work on an iPhone does anyone know?

No, you can't put Thunderbird on an iPhone, but I'm the iPhone has it's own email client built in.  Here's a link to set up the iPhone to use an IMAP account:
[http://allforces.com/2007/07/05/iphone-imap/](http://allforces.com/2007/07/05/iphone-imap/)

> 
Quote:
Neither of these are a home email server, that's a whole topic in itself.
What exactly is this? Is this where I register a domain name and use that as my email and use my home computer as the server?

Here's a basic how-to, but it's pretty involved:
[http://lifehacker.com/software/feature/how-to-set-up-a-personal-home-web-server-124212.php](http://lifehacker.com/software/feature/how-to-set-up-a-personal-home-web-server-124212.php)

---

### Post by PsychedelicWonders on 2008-08-07
thanks I appreciate the info.

So what advantages would there be to having a home email server?

Where can I find a walkthrough on setting up IMAP with thunderbird?

---

### Post by jimv on 2008-08-07
Here's a video walkthrough for setting up Thunderbird with Gmail's IMAP server.

[http://www.downloadsquad.com/2007/11/09/using-thunderbird-with-gmail-imap/](http://www.downloadsquad.com/2007/11/09/using-thunderbird-with-gmail-imap/)

---

