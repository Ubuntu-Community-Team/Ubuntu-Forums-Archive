---
title: "[SOLVED] Hardware details"
date: 2008-09-02
forum: General Help
---

### Post by colobix on 2008-09-02
HI all.
I wonder where and how I can find out all the details about my hardware card names etc?

Thanks:)

---

### Post by iaculallad on 2008-09-02
> **colobix said:**
> HI all.
I wonder where and how I can find out all the details about my hardware card names etc?

Thanks:)

On your terminal:

```
sudo lshw
```

---

### Post by colobix on 2008-09-02
Great!
Thanks:)

---

### Post by colobix on 2008-09-02
But that was very generel.
Isn't it possible to just get a list over graphic card or audio card ?

---

### Post by iaculallad on 2008-09-02
> **colobix said:**
> But that was very generel.
Isn't it possible to just get a list over graphic card or audio card ?

On your terminal:

-For Audio:

```
lspci | grep audio
```

-For Video:

```
lspci | grep VGA
```

---

### Post by colobix on 2008-09-02
Thank you very much:)

---

