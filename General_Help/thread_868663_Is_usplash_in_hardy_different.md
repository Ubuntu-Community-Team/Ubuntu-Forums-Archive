---
title: "Is usplash in hardy different?"
date: 2008-07-24
forum: General Help
---

### Post by Rurushu on 2008-07-24
I downloaded many splash themes, some are official...

Then copied both to /usr/lib/usplash

```
maya@maya-lp:/usr/lib/usplash$ ls
ubuntustudio-theme.so  usplash-linda-theme.so  usplash-theme-greenman.so
usplash-artwork.so     usplash.so              usplash-theme-ubuntu.so
```


Then I tried:

```
sudo update-alternatives --config usplash-artwork.so
```

...

```
There are 2 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/usplash/usplash-theme-ubuntu.so
*+        2    /usr/lib/usplash/ubuntustudio-theme.so

Press enter to keep the default[*], or type selection number: 


```

That's why when, in hardy, I try to link usplash-artwork.so to the new theme, I get text booting instead!!

It recognized the official themes only!!

Well, there is a difference in the structure of official themes and unofficial themes... because when I list the contents of the usplash folder, the official themes are black-colored while other themes are green-colored!!!

Any idea?

---

