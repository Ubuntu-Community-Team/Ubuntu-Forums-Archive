---
title: "Can't shut down my laptop if I'm logged on"
date: 2010-12-27
forum: Hardware
---

### Post by Fibonacci on 2010-12-27
Ever since I upgraded to Maverick, trying to shut down my laptop from the menu, if I'm logged on, just logs me out and gets me back to the GDM login screen. From there I can then shut it down normally.
This didn't happen under Lucid.

Does anyone else experience this? How can I solve it?

---

### Post by Fafler on 2010-12-27
Your issue is probably easily solved, but it's definitely not a hardware issue. Stuff like that just go wrong in the upgrade process from time to time. You might have better luck asking this in another subforum.

To make sure everything is upgraded correctly, open a terminal and do this:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Fibonacci on 2010-12-27
> **Fafler said:**
> Your issue is probably easily solved, but it's definitely not a hardware issue. Stuff like that just go wrong in the upgrade process from time to time. You might have better luck asking this in another subforum.

Well, I was thinking more "laptops" than "hardware", but perhaps you're right. Which would be an appropriate subforum?

> **Fafler said:**
> To make sure everything is upgraded correctly, open a terminal and do this:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

It seems to have solved it for now. Thank you!

---

### Post by Fafler on 2010-12-27
You shouldn't expect it to reappear. The textmode apt interface is a good way of installing and keeping your system up to date.

As to where to ask this kind of question, the Installation & Upgrade subforum would be a good choice.

---

### Post by Fibonacci on 2011-01-04
Well, it hasn't reappeared so I'm marking this as solved.
Thanks again.

---

