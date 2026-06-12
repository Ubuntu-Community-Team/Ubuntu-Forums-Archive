---
title: "[SOLVED] nonprintable characters botch console output"
date: 2008-08-18
forum: General Help
---

### Post by FatDave on 2008-08-18
In a console, either windowed or straight text mode, if I accidentally cat a binary file, the console's character set often changes to extended ascii characters (border pieces, shaders, special characters, etc.) You can look at man pages, file contents, anything in text mode will use a lot of ascii chars above 127.

For an example, try:

```
head /dev/urandom
```

About 50% of the time, all console output will be changed. Running the command a few more times will randomly fix it. I assume it has to do with the printability of the last character output.

Anyhow, is there an easy sure-fire way to fix this when it happens? This has perplexed me for as long as I've used linux, but when it happened today I figured I'd look for a fix. Didn't find one, so posting here.

Thanks.

---

### Post by Morpheun on 2008-08-18
```
reset
```

That will restore your console to its default settings. At least for bash, I'm not sure about other types.

---

### Post by FatDave on 2008-08-18
> **Morpheun said:**
> ```
reset
```

That will restore your console to its default settings. At least for bash, I'm not sure about other types.

Awesome! Would you believe I never learned that in like 13 years of using linux?

Thanks!

---

