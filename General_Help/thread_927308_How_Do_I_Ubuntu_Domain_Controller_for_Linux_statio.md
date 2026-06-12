---
title: "How Do I: Ubuntu Domain Controller for Linux station's"
date: 2008-09-22
forum: General Help
---

### Post by cyauch on 2008-09-22
First, please excuse me if I am posting in the wrong area.  Second, rather new to Linux, and even less with Ubuntu.  My experience started with openSuSE 10.2, and have decided upon Ubuntu 8.04.  To date, I am enjoying the heck out of it.  I've managed to get it running on both my laptop and desktop machine, and have even installed in on a desktop in the closet to act as my home server.  I've also gotten an HP PhotoSmart C4580 to both print and scan wirelessly using HPLIP, even though the C4580 support isn't there yet (if anyone needs to know how, I'm more then willing to pass info on :) .  

I've followed the instructions from Ricky Jones [http://www.rrcomputerconsulting.com/view.php?article_id=2](http://www.rrcomputerconsulting.com/view.php?article_id=2) (and posted in another link somewhere on this board), and successfully have the server running openLDAP and SAMBA.  From the command line (on my desktop), i can run smbclient -L //MY_SERVER_NAME_HERE and login as anon.  I'm a Windows person, and have always worked with MS Server's and PC software.  Therefore, I know lots about GPO's, Active Directory, and things of those nature, but am having several issues with the equivalent in Linux.  

My Questions: 

1.  If i am not going to be running any Windows workstations, then do i need LDAP installed and running?  Will SAMBA suffice? 

2.  How would i configure the Ubuntu server to act as the domain controller to validate user logins, and resource access (printers, additional drives installed in the server)?  And, how would i force Ubuntu desktop to validate against the controller instead of itself? There are tons of articles on how to get a windows client to authenticate against LDAP / SAMBA, but I would like to get away from windows altogether.  And, with respect to shares and permissions, what is the easiest way to do this?  I've got WebMin installed on the Ubuntu server. 

3.  With respect to patch management (Windows version is WSUS), is it possible to configure an Ubuntu server to push updates to client machines, rather than have each client validate, and rely on the user to update?  

My main focus right now is #2.  Once i can get my desktop to authenticate against the server, then I can setup the wife's PC to use Ubuntu, and not have MS software.  I've done some searching in these forums, but can't locate anything that resembles what i'm looking for (re: tons of threads to read, and would probably take forever :-) )  As I said, I'm a Windows server person, so while not a complete stranger to server environments, this is a challenge for me.  I don't mind using the command line either, if needed :-)  ) Thanks.

BTW, version of Ubuntu being used is 8.04 Desktop and Server version

---

### Post by yield999 on 2008-09-23
Hi Cyauch,

This is quite a nice question you have. I would like to do the same to have a Linux machine connect to a MS AD Domain... 

I will keep checking that thread for answers as well... 
P.S : Sorry to pollute your thread.

---

### Post by koenn on 2008-09-23
> **cyauch said:**
> 
My Questions: 

1. ...

2 ...

3....


complex question. 
I think your translating what you know from Windows to Linux, clouds things. You seem to be asking "how do I create a Microsoft Active Directory domain without Microsoft software on either servers nor workstations". The real question is : in such case, do you really need an AD (- look-alike) ? Or: what do you really want to achieve ?

re 1. AD authentication is great for single sign-on across multiple servers.  what's the purpose of having AD authentication if you have (apparently) only 1 server ?  I can think of only one advantage. Is that really worth the trouble ? 
Samba can handle access to file sharing just fine, but I don't know if it can handle all domain logins all by itself - you might need Kerberos, and possibly LDAP (which happen to be the protocols Microsoft AD also uses, be it in slightly non-standard implementations)

re. 2.  there are ways of joining Linux desktops to an MS AD Domain (eg [http://www.likewisesoftware.com/products/likewise_open/](http://www.likewisesoftware.com/products/likewise_open/) ), and there are ways to let a SAMBA server act as an AD Domain controller. Logically, you should be able to do both combined and join Linux workstations to a a Samba-controlled 'AD' domain. The question is: what's the added value of such a configuration ?


re 3. I don't think wsus actually pushes updates to clients, IRC it's the Windows Automatic Update Agent on the workstations that pulls updates from the server. apt and rpm do the same on Linux, it's their normal behaviour to get pacjages from network servers and install them. With a schedaled job (cron), you can automate it, and if you run a local repo (just a web server, basically), you have control over what gets installed. 

for remote management: you can do all kinds of stuff with remote shells and scripts, or look into professional sofware such as canonical's Landscape. [http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)

Still, Thinking about an all linux network in strictly Windows terms is probably not a good idea. You might find this an interesting read :
[http://users.telenet.be/mydotcom/howto/linux/migration03.htm](http://users.telenet.be/mydotcom/howto/linux/migration03.htm)

---

### Post by cyauch on 2008-09-23
Koenn, 

thanks for the response.  After re-reading what i posted, I might have been a little vague in what i'm looking for.  With your response, maybe I can make what I'm after a little more focused. 

I installed OpenLDAP and Samba, in hindsight I think, not fully understanding the server / client relationship in Linux.  Since that post, I've read more info regarding Samba, LDAP, and NFS.  But before I continue, the reason for running a Windows server and network at home is that I tried to mirror what was at work to certain extent because the job that pays my bills is being a Windows / SQL Server Admin / DBA.  So, if i could test GPO's and stuff that at home, it would help at work.  But, since I don't desire to do that anymore, I've decided to move on to Linux because it's fun and new, but don't intend to mimic work :-) 

So, at home i have no Windows machines - everything is now linux, with one machine setup as a server.  I was, however, able to join a windows client to Ubutnu server edition with no problem (did that just to see if i could :-) ) That machine now has Ubuntu Desktop.  

Because I'm from a windows server / client realm, i thought that i had to have a Liunx server / client setup also.  I'm finding that's not really the case, but I'm gonna stay on that path now.  

From what I've read last night on web, are the following constant: 

1. My wife and have our own PC's. 
2. We have a single laptop we use for graduate work / teaching
3. Our daughter has her own PC
4. we have PC in the closet that used to run Windows Server 2003, and managed printers, shares, network AV, and patch management. I used WSUS so that i new what patches / updates were being installed, and because we use it work
5.  All PC's run Ubuntu 8.04 Desktop, with the closet PC running the server version

Am i correct in assuming the following: 
1. I can remove LDAP and Samba from the Ubuntu Server?  If so, how? (the reason(s) why follow)

2. I can use NFS to manage all shares / resources within a linux environment?

3. In order for any of us to use shares / resources on the Ubuntu server, I will have to create our userID's on that server, matching our current userID and password? 

4. If, in the future, I have Windows machines, I will need some form of LDAP / Samba for those clients to use Linux resources on a server? 

To answer the question about 'what the added value?', I admit, running a DC in the house is a little over the top.  I guess for me its a 'personal' kinda thing in that I'm fairly weak with Linux and want to learn as much as I can.  I've had a few friends also make the switch, so we have a big learning thing going on.  As more and more people make the move to Linux, I feel the extra knowledge can't hurt :-)  

Yield999: If you want to connect Linux to an AD domain, I can dig up some of my notes and send them to ya.  Before I brought my 2003 server down, It was pretty easy to connect my desktop and laptop (running Ubuntu) to the AD and use its resources.  Course, GPO's and stuff like that won't apply, but it worked great with no performance issues.

---

### Post by yield999 on 2008-09-24
First,

Thank's to both of you. I have a lot of my questions answered here in theses post. 

Cyauh : I would be glad to have som of your notes about joining Linux machines to a MS AD Controller. I am currently building my new workstation using Ubuntu right now and would probably need soe of your advice if possible.

Best Regards !

---

### Post by yield999 on 2008-09-24
Sorry Double post.

---

### Post by koenn on 2008-09-24
> **cyauch said:**
> 
1. I can remove LDAP and Samba from the Ubuntu Server?
Yes, but see further

> **cyauch said:**
> 
 If so, how?

same way you (probably) installed them :```
 apt-get [--purge] remove openldap samba [...] 
```list all the packages you installed but don't need anymore. since you're interested in learning linux system administration : read the man page for apt-get 
(disclaimer: this is not a 'rtfm answer' :) )

> **cyauch said:**
> 
2. I can use NFS to manage all shares / resources within a linux environment?

Yes and No.
Yes: NFS is the native filesharing system for Linux/Unix, and suprisingly easy to set up, so in an all linux environment it would be your preferred choice.
No: it's a file sharing system, and nothing else. Like : it doesn't do printer sharing. Samba does file AND printer sharing because it's meant to mimic Windows File & Priter sharing + whatever MS has attached to those services. 

There are several approaches to network printing in a linux/unix environment. CUPS is, if I'm not mistaking, the current way to go.
[http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS](http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS)
or google for CUPS network printer or something like that.
(disclaimer: this is not a "google it" answer :) )
 
you should also read about ssh. it's a remote shell but can also be used to create secure channels for file sharing, file transfers, ...

> **cyauch said:**
> 
3. In order for any of us to use shares / resources on the Ubuntu server, I will have to create our userID's on that server, matching our current userID and password? 

Yes and No.
Yes, you do need to create accounts on both the server and the workstations. Here is where you lose the advantage of a central authority (LDAP, Kerberos). 
No, they don't need to be identical. It's possible to have jd with somePassword login to a PC, and from there log on to a server as johndoe with someOtherPassword, but it's easier on the user to not have to remember separate usernames and passwords, and (some) network services will not require a 2nd login if both accounts match.

Not all network services require a user account on the server (think : web server ..), and lots depends on how you manage permissions on the server.

Lastly, there are alternatives to password authentication (key pairs, certificates, ...) that can help to make things transparent to the users. 

You might want to start with just accounts and passwords, see how things go, and take it from there 

> **cyauch said:**
> 
4. If, in the future, I have Windows machines, I will need some form of LDAP / Samba for those clients to use Linux resources on a server? 
Yes and No
You'll need samba to provide file and printer sharing to Windows clients, yes.
Other resources ? Depends what. Some resources are pretty platform-independent (eg web pages); on the other hand, you might start deploying native Linux services that Windows has no way of interacting with.

You will not need LDAP, normally. Windows clients can be authenticated by Samba; they'll be prompted for username/pass when they access a share. 
Read the samba manuals (samba.org) - there's a whole chapter just on the different types of authentication and security schemes.

---

### Post by cyauch on 2008-09-28
Koenn, 

Thanks!  Been on travel for a few days.  Sorry it took a little while to respond.  

First, the article 'Dude, where's my Active Directory' was a great first-read, and was in a context for a complete Window person to understand and relate to.  Thanks for that link.  That doc is now in the front of my notes binder.  

Second, thanks for taking the time to cover my points one at a time.  The information you have provided has allowed me to refine some of my net searches for more specific information, and provided me with a plan to follow.  For what its worth, when i first started out with SuSE, the forums there were a little less patient with Linux noobs like me.  They may have changed since, but first impressions are everything, so again, thanks for taking the time to answer my questions, and provide links to read and build more net searches.  It's made it easier to map a Windows process (or not map) to the Linux platform and learn more about how it works.  

I plan on tinkering with Webmin and user's to see what I can come up with.  I think i',m gonna leave LDAP & Samba up cause occasionally family comes over with laptop's.  Since they run windows machines, I might just leave everything as is.  

Yeild999, 

Would be happy to help at anytime!  PM me whenever you have a question, or want to bounce ideas.  :D

---

### Post by mrojas73 on 2008-09-28
I don't know if you have seen this guide yet but it is what I do to setup what you are trying to achieve.
[http://www.rrcomputerconsulting.com/view.php?article_id=3]("http://www.rrcomputerconsulting.com/view.php?article_id=3")

---

### Post by cyauch on 2008-09-28
Thanks!  More info to add to my knowledge base.  For the record, I visited this site a number of times.  I don't know how i missed this listing.  Some good stuff there.  Thanks again!

---

### Post by koenn on 2008-09-29
> **cyauch said:**
> 
First, the article 'Dude, where's my Active Directory' was a great first-read, and was in a context for a complete Window person to understand and relate to.  Thanks for that link.  That doc is now in the front of my notes binder.

Thanks, glad you liked it.

> **cyauch said:**
> 
Second, thanks for taking the time to cover my points one at a time.  The information you have provided has allowed me to refine some of my net searches for more specific information, and provided me with a plan to follow.  For what its worth, when i first started out with SuSE, the forums there were a little less patient with Linux noobs like me.  They may have changed since, but first impressions are everything, so again, thanks for taking the time to answer my questions, and provide links to read and build more net searches.  It's made it easier to map a Windows process (or not map) to the Linux platform and learn more about how it works. 
As you "learn the lanuage" of Linux land, it will get easier to ask the right questions, and interpret the replies correctly. You sound like you can take that hurdle. 
Good luck, and have fun.

---

### Post by skierfrmct on 2008-11-02
[QUOTE=cyauch;5837971] I've also gotten an HP PhotoSmart C4580 to both print and scan wirelessly using HPLIP, even though the C4580 support isn't there yet (if anyone needs to know how, I'm more then willing to pass info on :) .  

I just purchased the same hp photosmart all-in-one printer after being told that most ever hp printer is on hplip...well i have just realized that is not the case...could you share with me how you got it up and running wirelessly?  
all the threads i have read point me to support for many other photosmart printers but not the c4580 specifically.  

i am also a linux and ubuntu noob so barney style (military for simplest) would be most helpful...

thanks in advance cyauch

---

### Post by cyauch on 2008-11-03
sure.  Here's what I did.  This is from a post i made over at Launchpad.net in the HPLIP area: 

Update: Using a combination of links and sites to piece information together, I believe the troubles I'm having are because the HP C4580 is not supported by HPLIP....yet. From what i understand, its being worked on though. But, for those that do have this printer / scanner, i finally go the scanner to work via wireless.

Again, I used hp-setup to install the printer. (download and install the HPLIP package).  After intall, 

sudo hp-setup
(OR)
sudo /etc/init.d/hp-setup
I do things a little differently on my box. 


When prompted, I selected Network, then next. It timed out on me. Then I selected the Manual button, and entered the IP address to the printer. I haven't been able to setup wireless initially on it via a Linux box (yet), so had to do it with a Windows box first. Once I was able to that, I have the printer a static IP address, and used address reservation on the router so it would always have the same IP for the following steps.  When i powered the printer down, it was a crap shoot on whether or not the printer would grab the same address.

Next, I filled in the location and description, and when prompted, I selected the PPD file for the C4400 series of printers. When completed, I printed a test page from the CUPS server. To date, the device does not show up in the HP device manager, but I can print, and the quality is great.  Note that the ONLY difference between the 4400 and 4500 series printes (that i have been able to find) is that the 4500 series have networking built in; either wireless or ethernet.  Other than that, they are the same an all other aspects (other than firmware upates)

For the scanner make sure the following packages are installed:

xsane
hpoj
hpoj-xojpanel
hplip
hpijs
hplip-gui

Next, type the following in console:

sudo /etc/init.d/hpoj setup

press ENTER for parallel and USB detection. when asked for JetDirect, enter the IP of the printer, WITHOUT a port number. This is important, as XSane would time out if i entered a 1,2, or 3. Just hit ENTER when prompted for a port number. You'll get a warning about not being to read a device string, but type Y then press ENTER when asked if you really want to add this device anyway. Press ENTER again to bypass setting up another device. When done, last line should read Starting the HP Office Jet Linux Driver and display the IP address. Now, open XSane and scan away!

Please let me know if you have any problems.  Thanks.

---

### Post by lenswipe on 2008-11-04
not sure if its of any interest but you could integrate the w2k3 server and the linux samba server. have he former for network AV and printers etc.. and the latter as a logon server ONLY :)

hope this helps


-L

---

### Post by skierfrmct on 2008-11-06
thank you cyauch!  i have just realized the the new hlip release 2.8.10 includes the hp photosmart c4580!!!everything is working as it should now that i downloaded and installed it.

---

### Post by rhotreads on 2009-05-25
> **cyauch said:**
> First, please excuse me if I am posting in the wrong area.  Second, rather new to Linux, and even less with Ubuntu.  My experience started with openSuSE 10.2, and have decided upon Ubuntu 8.04.  To date, I am enjoying the heck out of it.  I've managed to get it running on both my laptop and desktop machine, and have even installed in on a desktop in the closet to act as my home server.  I've also gotten an HP PhotoSmart C4580 to both print and scan wirelessly using HPLIP, even though the C4580 support isn't there yet (if anyone needs to know how, I'm more then willing to pass info on :) .  

I've followed the instructions from Ricky Jones [http://www.rrcomputerconsulting.com/view.php?article_id=2](http://www.rrcomputerconsulting.com/view.php?article_id=2) (and posted in another link somewhere on this board), and successfully have the server running openLDAP and SAMBA.  From the command line (on my desktop), i can run smbclient -L //MY_SERVER_NAME_HERE and login as anon.  I'm a Windows person, and have always worked with MS Server's and PC software.  Therefore, I know lots about GPO's, Active Directory, and things of those nature, but am having several issues with the equivalent in Linux.  

My Questions: 

1.  If i am not going to be running any Windows workstations, then do i need LDAP installed and running?  Will SAMBA suffice? 

2.  How would i configure the Ubuntu server to act as the domain controller to validate user logins, and resource access (printers, additional drives installed in the server)?  And, how would i force Ubuntu desktop to validate against the controller instead of itself? There are tons of articles on how to get a windows client to authenticate against LDAP / SAMBA, but I would like to get away from windows altogether.  And, with respect to shares and permissions, what is the easiest way to do this?  I've got WebMin installed on the Ubuntu server. 

3.  With respect to patch management (Windows version is WSUS), is it possible to configure an Ubuntu server to push updates to client machines, rather than have each client validate, and rely on the user to update?  

My main focus right now is #2.  Once i can get my desktop to authenticate against the server, then I can setup the wife's PC to use Ubuntu, and not have MS software.  I've done some searching in these forums, but can't locate anything that resembles what i'm looking for (re: tons of threads to read, and would probably take forever :-) )  As I said, I'm a Windows server person, so while not a complete stranger to server environments, this is a challenge for me.  I don't mind using the command line either, if needed :-)  ) Thanks.

BTW, version of Ubuntu being used is 8.04 Desktop and Server version
Hi Cyauch, I'd really appreciate knowing how you connected your C4580 printer to your network on hplip.  Any help appreciated.

---

