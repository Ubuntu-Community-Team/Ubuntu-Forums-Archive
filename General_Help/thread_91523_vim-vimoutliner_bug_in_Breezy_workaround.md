---
title: "vim-vimoutliner bug in Breezy workaround"
date: 2005-11-17
forum: General Help
---

### Post by avc on 2005-11-17
The vim-vimoutliner package in Ubuntu's repo has a bug. It just doesn't work. To get it working, you need to comment out these 3 lines (with a quote ") in /usr/share/vim/addons/ftdetect/vo_base.vim
```

"if exists("did_load_filetypes")
"  finish
"endif
```

Details here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=316626](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=316626)

---

### Post by byonk on 2006-10-29
ah, great, now its working! apparently hasn't been fixed in Dapper still but this takes care of it. thank you!

---

