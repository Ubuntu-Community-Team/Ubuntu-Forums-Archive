---
title: "[SOLVED] Extract filename from string in BASH - how?"
date: 2008-11-17
forum: General Help
---

### Post by Krupski on 2008-11-17
Hi all,

I have a small BASH script that I would like to add a function to.

Given a filename on the command line (returned in "$@"), I would like to extract all characters up to (but not including) the first dot character that may be in there.

For example, here's what I want:

Input: "scopeclock.asm" - Output: "scopeclock"

Input: "parser.asm.backup" - Output: "parser"

Input: "newprogram" - Output: "newprogram"

Input: "newprogram." - Output: "newprogram"

Input: "newprogram.bas" - Output: "newprogram"


I've Googled "bash scripting" until I got dizzy and couldn't seem to find anything that works. I'm sure it's easy to do.

Any help will be greatly appreciated!

Thanks!

-- Roger

---

### Post by geirha on 2008-11-17
${var%%.*} will remove everything starting from the first . 

```

for file in "$@"; do
  echo "${file%%.*}"
done

```

---

### Post by Krupski on 2008-11-17
> **geirha said:**
> ${var%%.*} will remove everything starting from the first . 

```

for file in "$@"; do
  echo "${file%%.*}"
done

```

Cool! Exactly what I needed. Thanks!

-- Roger

---

