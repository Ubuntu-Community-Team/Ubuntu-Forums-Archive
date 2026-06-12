---
title: "New here, having some problems"
date: 2005-11-19
forum: General Help
---

### Post by SkillZero on 2005-11-19
yo guys im new here as i said.
i have installed linux yesterday night and i have experienced some problems.
first: i cannot play MPG Files , i have tried the "Amarok" the "Tottem" and the default one.

second: i can't run **exe**cutable files, "Cannot display something.exe"
some people told me to install "Wine" but i tried and it says "package not found"

third: i cannot access to the files that i have mounted from windows , i dont have the "write" permission on the properties and cannot add it because "im not the owner"
i will be very glad if you can help me.

Cheers.


hey , a little edit , im not sure that im using ubuntu 5.10.

---

### Post by gerbman on 2005-11-19
[QUOTE=SkillZero]yo guys im new here as i said.
i have installed linux yesterday night and i have experienced some problems.
first: i cannot play MPG Files , i have tried the "Amarok" the "Tottem" and the default one.

second: i can't run **exe**cutable files, "Cannot display something.exe"
some people told me to install "Wine" but i tried and it says "package not found"

third: i cannot access to the files that i have mounted from windows , i dont have the "write" permission on the properties and cannot add it because "im not the owner"
i will be very glad if you can help me.

Cheers.


hey , a little edit , im not sure that im using ubuntu 5.10.[/QUOTE]

Hi, I think you'll find a good bit of information within these forums.  Here are some pointers:

1)  Make sure you have all the needed codecs installed.  See the [starter guide]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs").

2)  As you found out, Windows applications have no chance of running under LInux without help from another program (like Wine).  Wine seems to work for some, but my first suggestion is to make sure you can't find a version of the application designed to run under Linux.  If you still want to use Wine, make sure you have all the needed repositories added.  There is some info [here]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications").  

3)  From your wording, I am assuming you are trying to mount and write to a Windows partition.  If it is NTFS, I think the general consensus is that write support is a little sketchy at this point, and so I wouldn't recommend adding support for it (although there are guides on the forum if search for them).

---

### Post by SkillZero on 2005-11-19
fine. tnx alot man! ill try those guides out.

---

### Post by Chayak on 2005-11-19
Ubuntu comes stock with only free codecs, so follow the guide that was posted and everything should work fine.

---

### Post by SkillZero on 2005-11-19
fine , tnx. i still cant active but never mind,  i need to set myself as an owner.
any help?

---

### Post by taurus on 2005-11-19
You can use "sudo" to modify all the system files BUT if you really want to become root, then

sudo passwd root
(your password)
(root's password)
(re-type root's password)
su -
(root's password)

     Be warned!!!  You better know what you are going because one wrong command can trash your whole system...

---

### Post by SkillZero on 2005-11-19
ouch..tnx but no tnx ..afraid lol.
tnx for your help anyway =\
hmm..lets get back to another problem (i dont want to open new thread for nothing)
i have installed Xine media player and when i do right click on movies and then open with>
i dont see the Xine. why is that?

---

