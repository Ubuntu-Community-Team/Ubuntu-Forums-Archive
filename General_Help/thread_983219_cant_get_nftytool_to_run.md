---
title: "cant get nftytool to run"
date: 2008-11-15
forum: General Help
---

### Post by born2 on 2008-11-15
after installing nftytool and running typing ./nftytool -p phoenix -- -p phoenix -f 3.58 -e i was able to get it to run on a card reader now when i restart the system and try type ./nftytool -p phoenix -- -p phoenix -f 3.58 -e it wont run , if i type nftytool-1.1/ it says bash: nftytool-1.1/: is a directory so not sure were i need to go with this before i can set it to run on a system start up

---

### Post by mirak63 on 2008-12-23
in /etc/rc/local I had 

cd /opt/nftytool-1.1
/opt/nftytool-1.1/nftytool -p phoenix -- -f 3.58 -p phoenix -e

but you must use screen 

cd /opt/nftytool-1.1
screen "/opt/nftytool-1.1/nftytool -p phoenix -- -f 3.58 -p phoenix -e"

something like that

---

