---
title: "Adding users to Thinkfinger?"
date: 2009-02-08
forum: Hardware
---

### Post by Fishhooker on 2009-02-08
I've gotten everything about Thinkfinger set up, regarding it detecting my fingerprint reader and it reading my fingerprints...

However, when I want to add users to it, that's when the proverbial excrement hits the proverbial fan. Here's the terminal output when I try to add my username, "eli."

```
eli@eli-laptop:~$ sudo tf-tool --add-user eli

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Mode undefined.
Usage: tf-tool [--acquire | --verify] [--verbose] [bir_file]
  where --verbose and bir_file are optional.

  --verbose defaults to unspecified
    bir_file defaults to ~/.thinkfinger.bir.

eli@eli-laptop:~$ sudo tf-tool --add-user eli

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Two output paths specified, but you may only specify one:
  --add-user
  eli

```

What do I do?

---

### Post by cubical10 on 2009-02-23
I just ran into the same issue.

Did you every figure out a solution?

---

### Post by echo6 on 2009-06-30
The package is severly broken, with scripts in different locations to where the documentation suggests they should be.

I suspect the packages has been compiled without support for pam.

---

