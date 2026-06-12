---
title: "How to upload photos into specific directory structure?"
date: 2008-10-27
forum: General Help
---

### Post by NZJon on 2008-10-27
Hi,

I am trying to move away from using my current Windows based setup for saving my digital photos, but can't work out how to get my photos organised the way I'd like. I'd really like to store all my photos in a directory structure like this:

```

{year}/{month}/{year-month-day}/{filename}

```

The closest I can manage is using digiKam's "Auto-Create Albums" feature, but this only creates the {year-month-day} directory at the top level, which means the top level directory gets flooded with HEAPS of daily directories. 

Does anyone know a way--even maybe a shell script--that copies my photos off my camera, and creates the {year}/{month}/{year-month-date} directories as it goes? 

Many thanks,

  Jon

---

### Post by _sAm_ on 2008-10-27
Did you try F-spot?

---

### Post by NZJon on 2008-10-27
Hi _sAm_,

From what I've seen in F-Spot, it only uploads the photos into the root directory that you specify, so you get:

```

/blah/Photos/{filename}
/blah/Photos/{filename}
/blah/Photos/{filename}

```

... which isn't really what I'm after. Thanks for your suggestion though.

   Jon

---

### Post by thunderbirdje on 2008-11-09
Hm...

I'm using F-spot which creates a structure like:

```
/home/username/Photos/{Year}/{Month}/{Day}/filename.extension
```

Not 100% exactly what you want, but close I guess :D

---

### Post by NZJon on 2008-11-09
Hi _sAm_ and thunderbirdje,

I re-tried F-Spot in my clean install of 8.10, and it does indeed upload photos into a hierarchical structure. 

Many thanks for your suggestions.

Jon

---

