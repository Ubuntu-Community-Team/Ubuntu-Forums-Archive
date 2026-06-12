---
title: "problem compiling gaim cvs"
date: 2005-11-13
forum: General Help
---

### Post by kazu on 2005-11-13
I am actually trying to compile gaim from cvs, and while doing ./autogen.sh I have all ok include audio support but i can't manage to have a yes with audio/video support, could someone tell me the library I will have to intall ?

thanks for your time

KaZu

---

### Post by skyboy on 2005-11-14
can you post the result of autogen please ?
did you try ./configure already or autogen doesn't finish at all

---

### Post by CAE on 2005-11-14
Gaim CVS is missing gaim-vv (Gaim Video/Voice), but it does have interim support for limited voice communication.

---

### Post by skyboy on 2005-11-14
gaim-vv is in migrating process to CVS at the moment and it is not recommended to use gaim cvs version at the moment. 
> I'm Sean Egan, of the Gaim project.
 
 Please, please, please, please, please do not "switch to Gaim 2.0 as soon as possible."
 
 Gaim CVS is never for casual users, only for developers. It's almost always unusable, often straight-up broken, and has in the past destroyed users' data and settings, and permanently damaged their IM accounts (meaning they're IM accounts were broken on the server and couldn't be used with any client).
 
 Gentoo (*shudder*) decided to make a Gaim CVS ebuild. It was a complete pain for users, Gaim developers, and Sourceforge whose CVS system was crippled and had to be completely re-architectured (anonymous CVS is now completely separate from developer CVS). I realize Ubuntu wouldn't destroy Sourceforge like Gentoo (*shudder*) did, I'm just pointing out that bad things happen when distros ship CVS builds.
 
 It's also a huge pain for Gaim developers. I get IMed many times a day with duplicate "bug reports" about some feature which is far from complete in CVS. It's really bothersome to have to explain that they shouldn't ever use CVS. Ever.
 
 Real Soon Now, when we're confident Gaim CVS is fit for human consumption, we'll release some "Beta" or "Prerelease" builds. We will encourage adventurous souls to install it, use it, test it, break it, and feedback us.
 
 But, pretty, pretty, pretty please, don't ever give Gaim CVS builds to Ubuntu users. Please.
 
 -Sean Egan
 Gaim Developer, Ubuntu User

---

### Post by kazu on 2005-11-14
ok thanks for all your question

I was on their irc channel yesterday and in fact they are telling not to use the cvs actually because they know that their is some brokness and bug and to wait 2/3 weeks.

thks ;) and sorry to make u losse your time

---

