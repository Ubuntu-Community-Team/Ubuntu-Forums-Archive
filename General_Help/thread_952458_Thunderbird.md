---
title: "Thunderbird"
date: 2008-10-19
forum: General Help
---

### Post by cno on 2008-10-19
Hi. I couldn't find any posts on how to install thunderbird, though I'm sure there must be a good many such posts. Perhaps my searchingskills are just not so good.

So, I'm looking for some kind of guide or something like that which will tell me how to install thunderbird 2.0.

The real reason is that I can't seem to get the evolution mail to work with gmail. Rather the sending part doesn't work so if you know how to fix this it would be even better.

Cno

---

### Post by PsychedelicReaction on 2008-10-19
for installing thunderbird you just need to look for it in synaptic or use the command line

```
sudo apt-get install thunderbird
```

about the evolution issues, are you sure you configured it right?

```
smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587 
```

---

### Post by cno on 2008-10-19
> **PsychedelicReaction said:**
> about the evolution issues, are you sure you configured it right?

```
smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587 
```

No, I'm not sure, infact I'm quite sure I configured it wrong;) 

The code you wrote, do you just write it in terminal. Perhaps you could be a bit more specific.

Thanks for the help

---

### Post by PsychedelicReaction on 2008-10-19
> **cno said:**
> No, I'm not sure, infact I'm quite sure I configured it wrong;) 

The code you wrote, do you just write it in terminal. Perhaps you could be a bit more specific.

Thanks for the help

you have to put them in the evolution preferences, inside the account editor you can find the sending mail tab

---

### Post by cno on 2008-10-19
> **PsychedelicReaction said:**
> you have to put them in the evolution preferences, inside the account editor you can find the sending mail tab

Ok. Thanks

---

### Post by CPImmanuel on 2008-10-20
I have a created a problem with my Inbox in Thunderbird. I tried the Clamav anti-virus and it mistakenly quarantined my Inbox. When I started up Thundetbird, it did not have any of my mail prior to today. I did some digging, found the quanantined file, and put it into the correct directory, but it still does not appear to recognize it. Any way of getting my mail back? I do have a copy of the Inbox file..it is about 700 MB. Would uninstalling and reinstalling work?

Any help will be appreciated. 

Thanks,

---

### Post by pandamoniumcomputers on 2008-10-25
thanks PsychedelicReaction that was just the answer i was looking for.

---

