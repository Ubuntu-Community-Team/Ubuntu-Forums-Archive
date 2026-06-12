---
title: "Compiz-Fusion stop showing the title bars"
date: 2008-09-30
forum: General Help
---

### Post by ieBrazil on 2008-09-30
I don't know, you know, but it just stop appearing up there.

Last night I was changing some options on advanced desktop manager... and then it suddenly got that way. Too boring like this.

Help me, please.

Tnx.



ieBrazil


edit: I've got Ubuntu hardy heron 8.04.

---

### Post by Sycron on 2008-09-30
Can you give us a screenshot ?

---

### Post by ieBrazil on 2008-09-30
> **Sycron said:**
> Can you give us a screenshot ?

yap, here it goes.

---

### Post by Sycron on 2008-09-30
Open up a terminal and type ```
metacity --replace
```. Did you changed a theme ?

---

### Post by binbash on 2008-09-30
or emerald --replace if you are using compiz

---

### Post by ieBrazil on 2008-09-30
I don't know if it I am about to bring here up is a but, but anyway here it goes (sorry you all, I'm just coming and lay on this stuf):

- my Hardy Heron, after I started using Compiz-Fusion, stop showing the title bars and the window's borders.

Is that a bug thing? Tnx and if yes, try to help me! 

I have already done what other folks told me too ~ namely: installed Emerald manager, but got nothing.

Tnx! and sorry for any inconvinience.



ieBrazil

---

### Post by bwang on 2008-10-01
Have you run Emerald?
```
emerald --replace
```

---

### Post by anotherdisciple on 2008-10-01
> **bwang said:**
> Have you run Emerald?
```
emerald --replace
```

If you like the default GNOME window borders... you don't have to use emerald.

```
gtk-window-decorator --replace
```

---

### Post by anotherdisciple on 2008-10-01
I figured I would type my reply here even though you sent me a private message... this way everyone can benifit from it if we solve your problem.

Do this.... Hit Alt+F2 on your keyboard.

Type this command:

```
gtk-window-decorator --replace
```

If that doesn't work... type this:

```
emerald --replace
```


Also, in your compiz settings make sure that "Window Decoration" is checked. You get to these settings by going to (System > Preferences > Advanced Desktop Effects Settings)

---

### Post by ieBrazil on 2008-10-01
> **bigbrovar said:**
> dude how exactly is the problem .calm down and do a proper explaining so we can give a proper solution


Explanation? I tired and almost sick, as you English speakers say, of explaining the troubles!

The biggest of them: the windows on my laptop have NO title bars, no borders... and this implies several limitations to me - cannot resize as before etc.

...


tnx.

---

### Post by porchrat on 2008-10-01
> **ieBrazil said:**
> Explanation? I tired and almost sick, as you English speakers say, of explaining the troubles!

The biggest of them: the windows on my laptop have NO title bars, no borders... and this implies several limitations to me - cannot resize as before etc.

...


tnx.

I sometimes get that problem and I just change the "windows manager" under the compiz menu (the one under the compiz icon in the top right hand corner) from the one option to the other and then back again (GTK to metacity or something I can't remember the exact options and I'm not in front of the machine right now.

---

### Post by ieBrazil on 2008-10-01
> **anotherdisciple said:**
> I figured I would type my reply here even though you sent me a private message... this way everyone can benifit from it if we solve your problem.

Do this.... Hit Alt+F2 on your keyboard.

Type this command:

```
gtk-window-decorator --replace
```

If that doesn't work... type this:

```
emerald --replace
```


Also, in your compiz settings make sure that "Window Decoration" is checked. You get to these settings by going to (System > Preferences > Advanced Desktop Effects Settings)



I could do that if my Alt+f2 would work. Thats another command that stopped working properly. As well as Alt+f1.

U see my situation?

Plus I just checked: on System, Keyborad shorcuts, there I can see Alt+F1 on for Run Application... Edit again: sorry, I can see AltF2 there... also, Alft+f1 also does not work after that day..

---

### Post by bigbrovar on 2008-10-01
run this command in terminal and post the output ```
compiz --replace & emerald
```

---

### Post by Fc1032 on 2008-10-01
maybe the selected themes have no title bars. My current theme does not have a title bar.

Those visual effect programs can be confusing, but if you calm down and think slowly, it will all work out.

---

### Post by ieBrazil on 2008-10-02
> **anotherdisciple said:**
> I figured I would type my reply here even though you sent me a private message... this way everyone can benifit from it if we solve your problem.

Do this.... Hit Alt+F2 on your keyboard.

Type this command:

```
gtk-window-decorator --replace
```

If that doesn't work... type this:

```
emerald --replace
```


Also, in your compiz settings make sure that "Window Decoration" is checked. You get to these settings by going to (System > Preferences > Advanced Desktop Effects Settings)

Man, you're the one ~ it was all about Window Decoration option, alright. There is an option there... so now it's ok. Thank you very much! Just now I realized that... Tnx.




ieBrazil

---

### Post by Sycron on 2008-10-03
We'll it works now. Be happy.

---

