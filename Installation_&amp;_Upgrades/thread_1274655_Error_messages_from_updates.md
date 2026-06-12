---
title: "Error messages from updates?"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by dmfagan9 on 2009-09-24
Hi all-

I'm receiving this from updates and wondering if anyone can help me right this? 


W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/n/newt/libnewt0.52_0.52.2-11.3ubuntu1.1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/n/newt/libnewt0.52_0.52.2-11.3ubuntu1.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/n/newt/whiptail_0.52.2-11.3ubuntu1.1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/n/newt/whiptail_0.52.2-11.3ubuntu1.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/b/brasero/libbrasero-media0_0.9.1-0ubuntu3~intrepid1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/b/brasero/libbrasero-media0_0.9.1-0ubuntu3~intrepid1_i386.deb)
  Size mismatch


W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/b/brasero/brasero_0.9.1-0ubuntu3~intrepid1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/b/brasero/brasero_0.9.1-0ubuntu3~intrepid1_i386.deb)
  Size mismatch


W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.3-1ubuntu1~intrepid1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.3-1ubuntu1~intrepid1_i386.deb)
  Size mismatch


W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.3-1ubuntu1~intrepid1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.3-1ubuntu1~intrepid1_i386.deb)
  Size mismatch


W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.3-1ubuntu1~intrepid1_all.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.3-1ubuntu1~intrepid1_all.deb)
  Size mismatch


W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.4a-0ubuntu2~intrepid1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.4a-0ubuntu2~intrepid1_i386.deb)
  Size mismatch


Anyone have some insight into how I can fix this? Thanks so much

Dylan

---

### Post by dmfagan9 on 2009-09-24
So the updates went through after a few tries but now when i put this line into the terminal


sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

and then it asks me for my password- it wont let me type. I press the keys on the keyboard but nothing appears? Its locked? Suggestions?

Thanks
Dylan

---

### Post by Shazaam on 2009-09-24
Don't worry, the password is there. Hit your enter key after typing it in.

---

### Post by dmfagan9 on 2009-09-24
Thanks!

---

