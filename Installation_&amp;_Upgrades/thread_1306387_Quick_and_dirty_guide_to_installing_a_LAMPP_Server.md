---
title: "Quick and dirty guide to installing a LAMPP Server"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by velkymx on 2009-10-30
Step 1 install a linux server – such as Ubuntu Server 

Do not install any packages but the base system

Login to the command line…

Step 2 Install the MySQL server

We need to add this first. It will make step 2 configuration much much easier.

Use the command:

sudo apt-get install mysql-server

remember the password you put in for root.

Step 3 Install phpmyadmin

This will install all of the dependencies needed to run apache and php – you won’t need to install them separately. 

Use the command:

sudo apt-get install phpmyadmin



That’s it!

To test the installation...

You can now go to another computer on your network and check if it worked by typing: [http://IPOFYOURSERVER](http://IPOFYOURSERVER) and you will see the apache worked message. Also you can connect to the phpmyadmin tools by visiting [http://ipofyourserver/phpmyadmin/](http://ipofyourserver/phpmyadmin/)

Enjoy!



Source: [http://www.synergymx.com/page.php?Title=Quick_and_dirty_guide_to_installing_a_LAMPP_Server/]("http://www.synergymx.com/page.php?Title=Quick_and_dirty_guide_to_installing_a_LAMPP_Server/")

---

