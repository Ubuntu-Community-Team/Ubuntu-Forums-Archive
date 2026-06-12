---
title: "Evoultion mail help"
date: 2008-08-13
forum: General Help
---

### Post by jsblackmaro on 2008-08-13
Hello
I am using evolution mail with ubuntu 8.04 with my domain accounts.  I have about 12 of them.  I know its a lot...   But I have one setup, and it works fine..  But when I start adding multiples, it starts hanging, and not responding.  Can it be because it cant handle all the accounts?  I only loaded 6.  Any ideas?

---

### Post by gkaragoulis on 2008-08-13
I think I have an idea what it could be, and it's not that you have too many accounts (you have to give ubuntu more credit than that...)  Check your account settings on the first accounts you setup.  Check if you have the global address list server set to anything.  I seem to recall having similar issues with my 1 domain account when I left that field blank; it hangs trying to access the blank global address list.

---

### Post by jsblackmaro on 2008-08-13
I was knocking Evolution, not Ubuntu!!  I love using Ubuntu!  Where is this global address list box located?  I cant seem to find it.  What should it be set to, if it should not be blank?

---

### Post by jsblackmaro on 2008-08-13
adding to this.  I get this error log...

Failed to read valid greeting from Pop server (my Pop server)  Its sending and receiving, but thuis error is in the logs a tremendous ammount!

---

### Post by gkaragoulis on 2008-08-13
I think that POP error is unrelated, this has to do with your domain accounts.  To set the global address list, first go to the list that lists your domain e-mail accounts, then open one up and view its settings.  I don't have evolution in front of me but I'm sure it's somewhere in there.  When you find it you want to set it to the ip address/hostname of the domain controller, or whatever is hosting the global address list.

A sure-fire test of this is to try to search your global address book...that should crash it every time...it did to me...

---

### Post by jsblackmaro on 2008-08-14
I cant find anything related to a Global Address book in Evolution.  All I see under address books is on this computer Personal.  It is now not receiving mail on 3 accounts, and that error message is still coming up.

I was able to look into my addressbook, and search it..  But it didnt crash.  I am not hooking to exchange with this at all.  Im using my own domain, and my own host.

they all work perfectly in Thunderbird, but I cant sync my treo with thunderbird.  I can with evolution, and gnome-pilot..

---

### Post by tuxxy on 2008-08-14
Maybe this will help, someone has a problem with it slowing down due to lots of domains

[http://ubuntuforums.org/showthread.php?t=479810](http://ubuntuforums.org/showthread.php?t=479810)

---

### Post by jsblackmaro on 2008-08-14
I will take a look.  FYI  I am not using mutile domains.  Just one.

---

### Post by tuxxy on 2008-08-14
ok I see, did you try the howto aswell

[https://wiki.ubuntu.com/Evolution](https://wiki.ubuntu.com/Evolution)

---

### Post by jsblackmaro on 2008-08-14
I read that post...   It said to drop the frequency..  I staggered them in 10 minute intervals.  and if I go to the POP how-to, I get this..

    * EvolutionPopMail

This page does not exist yet. You can create a new empty page, or use one of the page templates.


Isnt that ironic??   dont you think!!!

---

### Post by tuxxy on 2008-08-14
oh sorry jsblackmarrow, I give the wrong link there seems I linked to the wiki :lolflag: 

Heres what I meant to post :)

[https://help.ubuntu.com/community/Evolution](https://help.ubuntu.com/community/Evolution)

---

### Post by jsblackmaro on 2008-08-14
That didnt really give me any help either.  Im going to try some things tomorrow.  Im going to hit the bed.  Got a headache looking at this.  Thanks for the help thus far..  Always a pleasure!!

---

### Post by jsblackmaro on 2008-08-14
Ok day 2....  I have removed all of the accounts in Evolution but one.  I designated the mail server as mail.domain.com.  I even have SSL setup with the incorrect parameters.  and it works just fine with one account.  the second I add multiples, it crashes out, and fails to fetch..

---

