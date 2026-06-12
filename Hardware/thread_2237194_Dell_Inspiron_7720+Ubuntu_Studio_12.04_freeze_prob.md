---
title: "Dell Inspiron 7720+Ubuntu Studio 12.04 freeze problem"
date: 2014-07-31
forum: Hardware
---

### Post by KarlHungus on 2014-07-31
hi, installed Ubuntu Studio 12.04 on  Dell Inspiron 7720.
[here's is specs]("http://www.laptopmag.com/review/laptops/dell-inspiron-17r-se-7720.aspx"), except i put ssd drive in mine

suddenly my computer started to freeze (no command can shut it down) 
before that fan works like crazy

i red that it might be problem related to that both the Intel and Nvidia video cards were running at the same time
[http://www.geek-tips.com/2013/08/08/ubuntu-13-04-on-the-dell-inspiron-17r-special-edition/](http://www.geek-tips.com/2013/08/08/ubuntu-13-04-on-the-dell-inspiron-17r-special-edition/)

her's suggestion to solve it by doing this:

sudo add-apt-repository ppa:bumblebee/stable

sudo apt-get update
sudo apt-get install bbswitch

modprobe -r nouveau
sudo sh -c 'echo "blacklist nouveau" > /etc/modprobe.d/nouveau-blacklist.conf'
echo "bbswitch load_state=0" >> /etc/modules
update-initramfs -u

but i got message that bbswitch package cant be located...

can somebody been in this situation?

i am total linux begginer
what this bumblebee solution means? to switch off native card and use nvidia?

i understand that i need to install driver for it myself:
tried this instruction:
[http://ubuntuhandbook.org/index.php/2014/04/install-nvidia-driver-331-67-ubuntu140](http://ubuntuhandbook.org/index.php/2014/04/install-nvidia-driver-331-67-ubuntu140)

everything was fine till 4.
when i needed to sudo service lightdm stop

after this command screen goes black and nothing happens
i feel lost in here :(

this is great laptop
hope there is a way to solve this fan problem and also fully use my video card, because
graphics was the reason i bought this machine

anyone, please?

---

