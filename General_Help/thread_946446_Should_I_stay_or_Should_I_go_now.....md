---
title: "Should I stay or Should I go now....?"
date: 2008-10-13
forum: General Help
---

### Post by amaturepro on 2008-10-13
Hi All,

I'm considering building a Ubuntu Desktop for some specific Purposes:

[LIST=1]
[*]E-Mail Server (With online web access)
[*]Media Storage with online access (Docs etc..)
[*]VMWare Server
[*]Media Centre Application
[*]Web Site Hosting
[/LIST]

I've rationalised with myself and I believe they are also in the order of importance. I've been looking around and I a gather a few points:

**Ubuntu** is a good distro to use, it has lots of stable software and a massive amount of help topics and forum users.

**Linux** in general has the ability better anything windows can do but requires more knowledge

**Ubuntu/Linux **distros are very stable their performance is excellant

**I'm** 90% sure windows is not the product I want to continue with and Mac Tower is too expensive



So on this basis I have a few questions which I hope somebody could help me with:

From the Above Points:

**1 - E-Mail Server (With online web access)**
Q - I know they are many products for this but can anybody recommend a stable yet pleasing on the eye product?

**2 - Media Storage with online access (Docs etc..)**
Q - I'll be using a RAID card in RAID 5 with 4x 750GB Seagate Drives - Any issues?

**3 - VMWare Server**
I think I've chosen VMWare [**_LINK_**]("http://www.vmware.com/products/server/")
Q - Any concerns?

**4 - Media Centre Application**
I'm sold on ENTERTAINER - I only want Video Playback, Music and Pictures and for the GUI to look good (Child friendly)  [**_LINK_**]("http://www.entertainer-project.com/")
Q - Can I set this app to be Full Screen and then login to the box via VNC without altering the Media Centre Screen being displayed (Multiple concurrent logins I guess is what I'm asking)?

**5 - Web Site Hosting**
Q - Built in to Ubuntu but what website building apps can I use (I have a MacBook so would guess I can use the built-in editor from that?)



If anybody has any experience or advice please shout up...

Regards
amaturepro

---

### Post by Sam on 2008-10-13
> **amaturepro said:**
> **1 - E-Mail Server (With online web access)**
Q - I know they are many products for this but can anybody recommend a stable yet pleasing on the eye product?
postfix + courier + [squirrelmail](http://www.squirrelmail.org/screenshots.php)

> **amaturepro said:**
> **2 - Media Storage with online access (Docs etc..)**
Q - I'll be using a RAID card in RAID 5 with 4x 750GB Seagate Drives - Any issues?
Does the RAID card do full hardware RAID ? In this case ok, but if not, it could be a good option to google if your card model works with linux.

> **amaturepro said:**
> **3 - VMWare Server**
I think I've chosen VMWare [**_LINK_**]("http://www.vmware.com/products/server/")
VMware works, but why don't you use VirtualBox OSE, which is open source ? It works very well.

> **amaturepro said:**
> **4 - Media Centre Application**
I'm sold on ENTERTAINER - I only want Video Playback, Music and Pictures and for the GUI to look good (Child friendly)  [**_LINK_**]("http://www.entertainer-project.com/")
Q - Can I set this app to be Full Screen and then login to the box via VNC without altering the Media Centre Screen being displayed (Multiple concurrent logins I guess is what I'm asking)?
I'm no expert at media center, but you can have multiple concurrent logins.

> **amaturepro said:**
> **5 - Web Site Hosting**
Q - Built in to Ubuntu but what website building apps can I use (I have a MacBook so would guess I can use the built-in editor from that?)
Use Apache for this. If you need a database use MySQL. [uhelp]community/ApacheMySQLPHP[/uhelp]

---

### Post by amaturepro on 2008-10-13
Hi Sam,

Thanks for the ideas.

1 - I've used Squirrelmail before (manu years ago) and was clunky, I'll have another look.

2 - My RAID Card is adaptec 2610sa raid (And quick search shows little results but no major concerns - Thanks)

3 - VirtualBox OSE is worth a look but VMWare Server is also free :0) 

4 - > I'm no expert at media center, but you can have multiple concurrent logins.
Sounds good...

5 - > Use Apache for this. If you need a database use MySQL. community/ApacheMySQLPHP 

This is also what I was looking at, thanks.


Thanks
Dan

---

### Post by ju2wheels on 2008-10-13
Performance wise, Virtualbox is much faster and less resource intensive than VMWare. I would highly recommending using it.

---

### Post by shawnrgr on 2008-10-13
> **amaturepro said:**
> Hi All,**4 - Media Centre Application**
I'm sold on ENTERTAINER - I only want Video Playback, Music and Pictures and for the GUI to look good (Child friendly)  [**_LINK_**]("http://www.entertainer-project.com/")
Q - Can I set this app to be Full Screen and then login to the box via VNC without altering the Media Centre Screen being displayed (Multiple concurrent logins I guess is what I'm asking)?

Might I suggest Boxee? Its new and still in Alpha but I've been using it for at least a month now with minimal issues. Last I checked of entertainer it wasn't really even functional yet. Beside Boxee's GUI and design technuiqes are beautiful, its a fork from the original XBMC project. Check it out [here]("http://boxee.tv")

---

### Post by jimv on 2008-10-13
If you're looking for a less clunky webmail interface, check out RoundCube.

[http://roundcube.net/](http://roundcube.net/)

---

### Post by amaturepro on 2008-10-13
> If you're looking for a less clunky webmail interface, check out RoundCube.

[http://roundcube.net/](http://roundcube.net/)

Round Cube looks good, my fav so far :0)   Thank You




> ju2wheels	

Performance wise, Virtualbox is much faster and less resource intensive than VMWare. I would highly recommending using it

Ok sounds like its worth a serious review... found this great [**_guide_**]("https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool") my only concern is porting my existing VMWare images . sounds like its possible.



> Might I suggest Boxee? Its new and still in Alpha but I've been using it for at least a month now with minimal issues. Last I checked of entertainer it wasn't really even functional yet. Beside Boxee's GUI and design technuiqes are beautiful, its a fork from the original XBMC project. Check it out here

Boxee looks good but their is very little info on the website, I guess they are waiting for 20th Oct to release the Beta when they will start to push it more.  I used XBMC when is first came out on my 1.3 xbox (and still going strong but demoted to the kitchen now using mc330 skin)

I think I'll try ENTERTAINER First as like the simple UI and I'm not after loads of fancy features just solid video playback and music image gallery.



THANKS ALL so far... some good products coming out... any more?

---

### Post by amaturepro on 2008-10-14
Hi All,

Going over something that Shawnrgr said:
> Might I suggest Boxee? Its new and still in Alpha but I've been using it for at least a month now with minimal issues. Last I checked of entertainer it wasn't really even functional yet. Beside Boxee's GUI and design technuiqes are beautiful, its a fork from the original XBMC project. Check it out here 

I started to look at XBMC as my media player... the only main concern I have with this is that XBMC only support x86. 

**Q- Due to this is their any 'off the shelf' solution to using x86 with 8GB Ram? **(I want to run 2 to 3 VM Images at times) and so really would like to use all my RAM

NB: I've seen PAE but it talks about kernal installs something I wanetd to aviod if poss as I've never used Linux before.


Thanks
aP

---

