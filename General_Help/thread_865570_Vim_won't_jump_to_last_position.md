---
title: "Vim won't jump to last position"
date: 2008-07-20
forum: General Help
---

### Post by jsmidt on 2008-07-20
I want Vim to jump back to the last position in the file when reopening the file.  I have this in my vimrc: (This came default with Ubuntu, just had to uncomment)

```
" Uncomment the following to have Vim jump to the last position when
" reopening a file
if has("autocmd")
  au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
    \| exe "normal g'\"" | endif
endif

```

As you can see I have the lines uncommented.  However, it still doesn't work.

Does anybody know why Vim still won't jump back to the last position?  Anything left to do?

---

### Post by Dr Small on 2008-07-20
Here is what mine says in /etc/vimrc on ArchLinux:
```
  autocmd BufReadPost *
    \ if line("'\"") > 0 && line("'\"") <= line("$") |
    \   exe "normal! g`\"" |
    \ endif
```

---

### Post by jsmidt on 2008-07-20
Thanks, but that code didn't work for me.  I wonder if I have some wired thing enabled somewhere on m system messing with vim.

---

### Post by lainlain on 2008-08-23
[https://bugs.launchpad.net/ubuntu/+source/vim/+bug/69611](https://bugs.launchpad.net/ubuntu/+source/vim/+bug/69611)

---

### Post by kiyodaira on 2009-04-20
check the permission of .viminfo under your home directory to be sure that you have the write privilege to this file.

---

### Post by ejricha on 2010-01-19
Thank you very much, I have had this problem for a while and I never really knew why.  Turns out that my .viminfo was owned by root for whatever reason.  Changed that and it jumps back perfectly.

---

### Post by tiga2001 on 2010-06-01
> **kiyodaira said:**
> check the permission of .viminfo under your home directory to be sure that you have the write privilege to this file.

Thanks, this helped me, too. Mine was also owned by root.

---

