---
title: "CLI Gmail Checker?"
date: 2008-11-20
forum: General Help
---

### Post by transmition on 2008-11-20
Does anyone know of a python/shell script/application that would allow me to check if I have any emails from the command line? So I would type something like "gmailchecker" and it would say "You have 5 new emails..."

Any help would be appreciated.

---

### Post by whitethorn on 2008-11-20
this is a script I use to check my imap accounts in conky, but it also works in the terminal.

> 
#! /usr/bin/env ruby
# by Ardanwen

require "net/imap"

imap = Net::IMAP.new("imap.gmail.com","993","true")
imap.login("username","password")
imap.select("Inbox")
value = imap.search(["NOT","SEEN"])
if value.empty? == false
   printf "#{value.nitems}"
else
   printf "0"
end
imap.disconnect

I called this file gmail.rb. Then youjust have to run the file.

```
ruby gmail.rb
```
For it to run, you need to install ruby you can find it in synaptic.

---

