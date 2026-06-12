---
title: "Beta to Final. How?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by tjeremiah on 2009-04-23
I've been a beta tester since day one. I want to upgrade to the final release of 9.04. Did an update and still in beta. How do I get to final?

---

### Post by drs305 on 2009-04-23
Normal updates should do it. Perhaps your server hasn't uploaded the final few files yet.

---

### Post by coffeecat on 2009-04-23
> **tjeremiah said:**
> Did an update and still in beta.

Can you enlarge on what you mean? Have you fully updated today? If so, you are running final. Why do you think you are still running Beta.

---

### Post by tjeremiah on 2009-04-23
nevermind. Just did another update after resetting and its solved.

---

### Post by Sashin on 2009-04-23
I don't have any updates. How do you tell if what you have is Beta or final?

---

### Post by drs305 on 2009-04-23
> **Sashin said:**
> I don't have any updates. How do you tell if what you have is Beta or final?

System, Administration, System Monitor. It will show "Ubuntu 9.04 (jaunty)"

---

### Post by JK3mp on 2009-04-23
Sorry didn't see above post.

---

### Post by Tim Sharitt on 2009-04-23
You may want to do
```
sudo apt-get dist-upgrade
```

just to make sure there are were no new packages added or old packages removed.

If you have kept up to date, you shouldn't have many (if any) package upgrades as everything should have been frozen in the days prior to the official launch.

---

