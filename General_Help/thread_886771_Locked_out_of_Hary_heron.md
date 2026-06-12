---
title: "Locked out of Hary heron"
date: 2008-08-11
forum: General Help
---

### Post by el10 on 2008-08-11
Sometime ago I installed Ubuntu Hardy heron on my laptop. Today I thought I would look at it, but it will not let me in, as it asks me a username and a password. I do not remember either

---

### Post by OutOfReach on 2008-08-11
When the GRUB menu comes up when you first boot your computer select the recovery mode. Ubuntu will boot up, but it won't ask you for a password since it is logging in as root. Then type in ```
passwd <YOU_USER_NAME_HERE>
```

---

### Post by el10 on 2008-08-12
Thank you for your help. I managed to get in. The date was not right I tried to correct it but asked for "authentication" and I could not be authenticated. may I get in as root and update the clock ?  how ?
thanks.
PS I like your "proud  Ubuntu user" Is this what is called a signature?

---

### Post by WRDN on 2008-08-12
> **el10 said:**
> Thank you for your help. I managed to get in. The date was not right I tried to correct it but asked for "authentication" and I could not be authenticated. may I get in as root and update the clock ?  how ?
thanks.
PS I like your "proud  Ubuntu user" Is this what is called a signature?

Open System > Administration > Users and Groups. Then click Unlock and enter your password. Now, click your username, Properties and the User Privileges tab. Ensure that the "Administer the System" check box is checked. This will allow you to perform the administrative tasks.

As for the latter question, yep, that's signature. To edit yours, click "User CP" at the top of the forum page, and select "Edit Signature" from the control panel.

---

