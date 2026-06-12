---
title: "Update Failed"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by sudhirnair on 2009-02-21
I'm trying to update packages using sudo apt-get update but I keep getting the error message shown below:

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

There is much more of this and then this comes:

Reading package lists... Done                          
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

Finally the ending message is:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

Please help me out with this problem. I'm using Ubuntu 8.10. Just started using it so I don't have much idea about what I should be doing. Thnx in advance!

---

### Post by sudhirnair on 2009-02-21
OK. I managed to get it working. The problem was I hadn't setup my proxy for Synaptic Manager :)

---

