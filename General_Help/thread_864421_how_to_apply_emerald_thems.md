---
title: "how to apply emerald thems"
date: 2008-07-19
forum: General Help
---

### Post by Killwa on 2008-07-19
i downloaded themes that it's from emerald type but the problem is i really don't know how to apply it in ubuntu 8.04

i am new in Ubuntu and i love it, it's very useful system.:)

---

### Post by irshadcharm on 2008-07-19
Run emerald --replace in the terminal

---

### Post by Killwa on 2008-07-20
i don't know how to run it from terminal.so please if you know could you tell me .

thanx

---

### Post by JagDragon on 2008-07-20
Run the following code in a terminal:
```
sudo apt-get install compizconfig-settings-manager emerald
```

An "Emerald Theme Manager" entry should come up under the System->Preferences menu, and you can install and manage multiple themes from there.

---

### Post by Killwa on 2008-07-21
thanx guys for comment

i did download emerald themes manger and it's work but the problem acutely it doesn't activate the theme.

maybe i don't know how to mange the them, could someone tell me?

---

### Post by JagDragon on 2008-07-21
You have to enable the effects. To do this, go to System->Preferences->Appearances. Open the "Effects" tab, and set it to "Custom". After that, reopen "Emerald Theme Manager" and try to reapply the theme.

Also, play around with "Advanced Desktop effects settings" to get some real cool things going on (Desktop cube and the like).

---

### Post by kidux on 2008-07-21
> **Killwa said:**
> thanx guys for comment

i did download emerald themes manger and it's work but the problem acutely it doesn't activate the theme.

maybe i don't know how to mange the them, could someone tell me?

Did you use the manager to import the theme? It won't show up until you do that.

---

### Post by mcduck on 2008-07-21
> **Killwa said:**
> thanx guys for comment

i did download emerald themes manger and it's work but the problem acutely it doesn't activate the theme.

maybe i don't know how to mange the them, could someone tell me?

Actually on some setups the themes activate when you click them in the Emewrald Theme MAnager, but on others you need to run "emerald --replace" to reload Emerald before the theme is activated.. This far I haven't found out the reason for this..

So, try running "emerald --replace" after selecting the theme you want.

---

### Post by Killwa on 2008-07-21
thanx guys i really appreciate that

i try to run emerald --replace and it's work.

you are a helpful people.

thanx again:)

---

