---
title: "$HOME/.dmrc"
date: 2008-09-18
forum: General Help
---

### Post by honkey on 2008-09-18
$HOME/.dmrc dosent exist notifier at booting

---

### Post by iaculallad on 2008-09-18
Drop on your terminal and issue the following commands below one-at-a-time:

```
sudo chmod 644 ~/.dmrc
sudo chown your_username ~/.dmrc
sudo chmod -R u+rwX,og-rwx /home/your_username
sudo chown your_username /home/your_username

```

EDIT: If it does not exist, try creating one:

```
touch ~/.dmrc
sudo chmod 644 ~/.dmrc
sudo chown your_username ~/.dmrc
sudo chmod -R u+rwX,og-rwx /home/your_username
sudo chown your_username /home/your_username

```

---

### Post by -Zeus- on 2008-09-18
I have no idea what that means but i don't have one either...

---

### Post by ronnielsen1 on 2008-09-18
chmod 700 /home/<yourusername>
chmod 644 /home/<yourusername>/.dmrc

I found this from googling. Do you have a .dmrc in your hidden files in your /home?

[http://www.ubuntuproductivity.com/journal/ubuntu/08/2008/fix-ubuntu-dmrc-permissions-error-on-login/](http://www.ubuntuproductivity.com/journal/ubuntu/08/2008/fix-ubuntu-dmrc-permissions-error-on-login/)

---

