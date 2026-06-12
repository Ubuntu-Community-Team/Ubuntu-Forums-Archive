---
title: "Ignore key strokes altogether"
date: 2011-05-09
forum: Hardware
---

### Post by Morrighan on 2011-05-09
I've been searching for answer for quite a while now. I found things that help but not entirely. So here's the deal:

I'm having an ongoing problem with the left winkey on my laptop. The laptop reads frequent key strokes even though the key is not being touched. I know you can re-map it to do nothing, and I do use the following command on start-up:

```
xmodmap -e 'keycode 133='
```But it still affects the system. When I open menus and go over the items the highlighted item blinks and runs up and down the menu and won't let me select (it usually closes the menu if I try to click on something). When I run xev, I can still see event from this key being logged.

I'm absolutely sure the key is the culprit, because when I booted my laptop with the key physically pressed all the time, it haven't gone crazy like usually and the menus functioned perfectly.

I'm running Kubuntu 11.04, but had the same exact problem on 10.10 .
Is there something I could do to make Kubuntu **completely** ignore any event triggered by this key? Not just re-mapping?

Thanks in advance.

---

### Post by Morrighan on 2011-05-11
No takers? I swear I tried to search for this. This problem really bugs  me, because right now I can't right click on anything and use the menu. I  have found new appreciation for those little menus, they make life so  much easier.

---

