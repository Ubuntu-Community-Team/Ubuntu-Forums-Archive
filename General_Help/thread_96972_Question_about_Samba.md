---
title: "Question about Samba"
date: 2005-11-30
forum: General Help
---

### Post by dnewburg on 2005-11-30
I finally had my Ubuntu box running great, or at least I thought I did.  I'm running Samba so that the wife's XP box can print to the serial laser printer on my machine wireless.  I rencently got my box up and running wireless (WPA, a challenge in it self), and now the windoze machine can't see my samba server at all.  I do have Firestarter installed, but I first configured it for my wireless card, ath0, and then just stopped it all together to see if that was the issue, but the XP machine still can't see it.  

Should running a wireless internet connection limit my ability to have a Samba server running on my machine?  Is there a way to solve my problem?

---

### Post by HighPlainsDrifter on 2005-11-30
[QUOTE=dnewburg]Should running a wireless internet connection limit my ability to have a Samba server running on my machine?[/QUOTE]

The answer to that is no. Samba does not care what medium you are using.

[QUOTE=dnewburg]Is there a way to solve my problem?[/QUOTE]

Have you edited the smb.conf file for the same workgroup as the XP box? (Or vice-versa?). Can you ping one computer from the other?

---

### Post by dnewburg on 2005-11-30
Thanks for the response...  I have both boxes on WORKGROUP, and no, I can not ping from either computers.  Both boxes indicate that packets were rejected, even when I take Firestarter down and I ping from the Windoze box out to my Ubuntu box.  I had the server working before, when I was running only a wired connection, but since the change to wireless, everything has dropped.

I appreciate any help.

---

