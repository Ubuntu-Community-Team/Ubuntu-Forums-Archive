---
title: "mail command"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by hyperAura on 2009-07-28
hi guys, can u help on which package to install to be able to use the mail command??
thnx

---

### Post by wojox on 2009-07-28
heirloom-mailx
mailutils

---

### Post by hyperAura on 2009-07-28
thnx for that..

to send i mail 

#mail [email]asdfgdsg@mail.com[/email]
then i put subject 
and then i put the content of the mail

to interrupt the mail i do Ctrl+C but if i do it twice i get a dead.letter and the mail is not sent..

wats the right way to interrupt??

---

### Post by wojox on 2009-07-28
Try this to see if it works:

```
mail -s “Hello world” you@youremailid.com
```

---

### Post by hyperAura on 2009-07-28
mail -s &#8220;Hello world&#8221; [email]you@youremailid.com[/email]
it does not seem to work like that for me :(

Cannot parse address `world&#8221;' (while expanding `world&#8221;'): Format of RFC822 object is bad

even if i write them the other way round the subject with the email i get the same result

do i have to put the another option to be able to insert my email address on the same line?

---

### Post by hyperAura on 2009-07-28
well if i put only one word as a subject i dont get a message but i dont send an email either..

how can i receive an email if i dont specify the email of the sender??

mail -s &#8220;Hello world&#8221; [EMAIL="you@youremailid.com"]you@youremailid.com[/EMAIL]

on this command is it the senders email or the recipients email??

i tried my email on both, this command and on the CC but i still dont manage to get a mail..

also how do u close the message after u finish writing it?? is it Ctrl+D ? thnx

---

### Post by wojox on 2009-07-28
type

```
mail --help
```

---

### Post by hyperAura on 2009-07-28
i tried everything unfortunately i didnt manage to send a mail though..

i tried   #mail -s -r "subject" sender@mail recipient@mail 
but does not work.. 
also for closing the message i tried either Ctrl+D or just a "." dot

I tried also mailx with the same parameters and everythin but does not work
i read the manual but i cant find anythin else that i might be doing wrong..

---

### Post by sorel on 2010-06-15
and how do you check the messages, and config POP?

---

