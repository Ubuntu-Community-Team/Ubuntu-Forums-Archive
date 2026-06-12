---
title: "[SOLVED] file not in PATH, gem executables will not run"
date: 2008-11-28
forum: General Help
---

### Post by mamboze on 2008-11-28
Hi,
I've installed gems for merb - a Ruby web framework and I get these error messages:
WARNING:  Installing to ~/.gem since /usr/lib/ruby/gems/1.8 and
	  /usr/bin aren't both writable.
WARNING:  You don't have /home/roy/.gem/ruby/1.8/bin in your PATH,
	  gem executables will not run.
When i run merb, I get an error message 
$ merb-gen app ruby_bookshop
bash: merb-gen: command not found

I tried to make the above files writable but I couldn't save the file permissions I changed as root. 
Could anybody tell me where I can find PATH ?
Any help much appreciated.

---

### Post by taurus on 2008-11-28
Just add these two lines to the end of your ~/.bashrc.

```

PATH=$PATH:/home/roy/.gem/ruby/1.8/bin
export PATH

```
Save it and run

```
source ~/.bashrc
```

---

### Post by mamboze on 2008-11-28
Hi taurus,

It worked perfectly. Thank you very much for your very prompt help. It's much appreciated. 

Roy

---

### Post by giac0m0 on 2011-10-05
Hello Taurus, following your instructions on 11.04 but it didn't work for me (I changed the path to my home directory).  I got no responses from adding the lines to .bashrc or running the script using the 'source' command.

---

### Post by nothingspecial on 2011-10-05
Hi, please make a new thread rather than digging up old ones.

Thanks.

Closed.

---

