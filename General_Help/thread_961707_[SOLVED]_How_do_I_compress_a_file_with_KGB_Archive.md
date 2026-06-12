---
title: "[SOLVED] How do I compress a file with KGB Archiver?"
date: 2008-10-28
forum: General Help
---

### Post by Rytron on 2008-10-28
Hi,
How do I compress a file with KGB Archiver?
I want the maximum compression.
Thanks.

---

### Post by Rytron on 2008-10-30
I figured it out.
I used this code:
```
kgb -9 archive1.kgb ZX_Spectrum.html
```

I compressed a webpage from 145kb to 20kb as an example.

This is the maximum compression setting.

The archive1 part can be called anything.

Decompression: ```
kgb archive.kgb
```

Table of contents: ```
more < archive.kgb
```

**argument** - **memory usage**	
 -0       	 2 MB - (the fastest compression)
 -1       	 3 MB
 -2       	 6 MB
 -3       	 18 MB - (dafault)
 -4       	 64 MB
 -5       	 154 MB
 -6       	 202 MB
 -7       	 404 MB
 -8       	 808 MB
 -9       	 1616 MB - (the best compression)

---

### Post by RealG187 on 2009-06-15
Is this real? Compress a 500 MB file into 1 MB?

---

### Post by karthick87 on 2010-03-11
How to decompress the file?

```
kgb archive.kgb <compressed filename>
```

Is this correct..?

---

### Post by Rytron on 2010-03-12
Decompression:

```
kgb archive.kgb
```

---

