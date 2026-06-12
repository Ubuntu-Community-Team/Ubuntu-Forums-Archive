---
title: "How to Swich Default Language In Hardy"
date: 2008-12-01
forum: General Help
---

### Post by lukjad on 2008-12-01
I have a classmate who installed Ubuntu 8.04 on his PC. He has put the Default language in Chinese (Which, fortunately, he speaks). He now wants to switch the account to English, menus, programs, etc.

Could you give me a step by step list that I can give to him?

Thanks.

---

### Post by Elfy on 2008-12-01
As far as I know it should just be System >Admin > Language Support

Add English - could remove Chinese or set English as default

---

### Post by lukjad on 2008-12-01
He says that he did that and there was no effect, even after a reboot. He created a new account with English as the language, and it works fine. He just can't seem to change this one.

---

### Post by sisco311 on 2008-12-01
```
sudo aptitude install language-pack-en language-support-en
```

he can select the language at the login screen.

---

### Post by Elfy on 2008-12-01
mm not sure then - found this in another thread dealing with similar

> I agree that adding language support through System ... Language
Support has odd results. From my experience, the stable way
to do it is adding the support and pack packages through
synaptic.

---

### Post by Icebear on 2008-12-01
at the log in prompt click options (if i rememeber correctly the write wording)

Then choose language. 

Choose english (of course you need to have English installed first) then you should get a prompt asking if you want this to be the default language click yes:)

---

### Post by lukjad on 2008-12-01
Thanks. I'll go through these steps with him to make sure he does them.

---

