---
title: "Quod Libet won't launch"
date: 2008-11-19
forum: General Help
---

### Post by dbbolton on 2008-11-19
I've been using Quod Libet from the repos, but I decided to test out version 2.0 from here: [http://code.google.com/p/quodlibet/](http://code.google.com/p/quodlibet/)

I did so by launching a python script inside a directory called ~/quodlibet-2.0 . I played with it and quit the application. But now I can launch /usr/bin/quodlibet and instead get this error:

```

Supported formats: mod, mp3, mp4, mpc, spc, trueaudio, wav, wavpack, xiph
Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 304, in <module>
    main()
  File "/usr/bin/quodlibet", line 33, in main
    library = load_library()
  File "/usr/bin/quodlibet", line 258, in load_library
    lib = library.init(const.LIBRARY)
  File "/usr/share/quodlibet/library/__init__.py", line 38, in init
    library.load(cache_fn, skip=formats.supported)
  File "/usr/share/quodlibet/library/_library.py", line 124, in load
    try: items = pickle.load(fileobj)
ImportError: No module named formats.mp3


```

Any suggestions?

---

### Post by dbbolton on 2008-11-20
Ok, I got it. I had to remove my ~/.quodlibet folder. This is kind of a pain because now I have to reconfigure all my plugins, but oh well.

---

