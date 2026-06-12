---
title: "Check IP Address with Bash"
date: 2008-08-11
forum: General Help
---

### Post by lyric0n on 2008-08-11
Hi,

I would like to check if I have received an IP address before moving on in a certain script, but I am having some trouble, here's what I've got.

str=$(ifconfig eth0 | grep "inet")
if [ ${#str}>0 ];
 then echo "true"
fi

But, this will always return true, even when 'echo ${#str}' shows 0, does anyone have any ideas or a better way to go about this?

TIA.

---

### Post by fahadsadah on 2008-08-11
Use str=$(ifconfig eth0 2>/dev/null)
This will be null if you don't have an IP, something other than null if you do.

---

### Post by lyric0n on 2008-08-11
Hi,

I tried this, but it doesn't seem to work. It just dumps the entire result of the ifconfig eth0 into $str, not just limited to the IP address. I tried str=$(ifconfig eth0 | grep "inet" 2>/dev/null) but I still just receive a 0 and not a null.

---

### Post by lyric0n on 2008-08-11
It looks like it was trying to string comparions, not integer, this fixed it:

str=$(ifconfig eth0 | grep "inet")
if [ ${#str} -gt "0" ];
then echo "true"
fi

---

