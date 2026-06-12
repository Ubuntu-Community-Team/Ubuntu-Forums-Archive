---
title: "Mailbox status"
date: 2008-09-25
forum: General Help
---

### Post by gerases on 2008-09-25
Hello,

I'm using a regular unix mailbox (flat file) and mutt for my email. I'm also using the gnome mail-notification plugin that shows an envelope when a new mail arrives. That's all good but sometimes I want the envelope to disappear (e.g. when I click on it) because I don't always have time to read my email right away. So that envelope keeps sitting there until I open mutt and unset the new flag on the message.

What I would like to do is click the envelope, run a bash script that would have the same effect as running mutt would. But I can't figure out what triggers mail-notification to display and remove the envelope.

I tried running stat on the mailbox but I see nothing special in the state of the file when the mail arrives and when it's read. It would be awesome to be able to remove the message right from the plugin, but it seems that that functionality is only available when the plugin is coupled with evolution. I might be wrong on this one.

Thanks for any thoughts...

---

### Post by gerases on 2008-10-02
So, no ideas? Is there an alternative mail notification tool then?

---

### Post by gerases on 2008-10-03
For now I created this function and made an alias to it.

 mutt -e 'push "<tag-pattern>~N\r<toggle-new><quit>"'

I also wrote a quick ruby script to insert "Status: RO" into the header of new messages, but I have doubts about the safety of running that script because as it's modifying the mbox file, my delivery agent (Exim) might be delivering a message. I do lock the file but I'm not sure if Exim looks at the lock, although I'm pretty sure it does. Still, the mutt approach is safer. I wonder how they solve the locking problem.

---

