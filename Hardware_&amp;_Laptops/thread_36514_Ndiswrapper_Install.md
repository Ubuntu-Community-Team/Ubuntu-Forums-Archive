---
title: "Ndiswrapper Install"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by avatar_58 on 2005-05-23
I have all the drivers ready to install my wireless nic (I've done it before in fedora) but I'm having trouble in ubuntu.

It keeps complaining about not finding the kernel source when I try to 'make', so i was told to get the linux header for my kernel (2.6.10-5-amd64-generic) and I did a 'dpkg -i' and they apparently installed. Unfortunately I get the same error.

Am I doing something wrong? Do I need to download the entire source?  ](*,) 

I was told there were deb files out there for ndiswrapper that could do everything for me, but I can't seem to find them. Can anyone help me?

I don't have any internet access via ubuntu so apt won't help me, I need to download to my flash drive (it works in ubuntu) and do it that way.

---

### Post by jkndrkn on 2005-05-23
This may help: [http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

---

### Post by avatar_58 on 2005-05-23
It helps (I found that one) but this is where I cannot go further:

"apt-get install build-essential fakeroot linux-headers-$(uname -r)"

Since I do not have internet access.... :-#

---

### Post by avatar_58 on 2005-05-23
N/m....however now I get this error while trying to 'make deb'


root@ubuntu:/usr/src/ndiswrapper-1.2rc1 # make deb
make[1]: Entering directory `/usr/src/ndiswrapper-1.2rc1'
make -f debian/rules binary-utils
make[2]: Entering directory `/usr/src/ndiswrapper-1.2rc1'
sed -e 's/-#KVERS#//g' \
-e 's/#NDISVERS#/1.2rc1/g' \
-e 's/#DATE#/'"`date --rfc-822`"'/g' \
        -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
        debian/changelog.template > debian/changelog
sed -e 's/#NDISVERS#/1.2rc1/' \
-e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
debian/control.utils > debian/control
echo "utils/loadndisdriver /sbin" > debian/ndiswrapper-utils.install
echo "utils/ndiswrapper /usr/sbin" >> debian/ndiswrapper-utils.install
echo "utils/ndiswrapper-buginfo /usr/sbin" >> \
        debian/ndiswrapper-utils.install
cp debian/dirs.utils debian/dirs
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installdocs
cp: cannot stat `README': No such file or directory
dh_installdocs: command returned error code 256
make[2]: *** [common-prolog] Error 1
make[2]: Leaving directory `/usr/src/ndiswrapper-1.2rc1'
make[1]: *** [binary] Error 2
make[1]: Leaving directory `/usr/src/ndiswrapper-1.2rc1'
make: *** [deb] Error 2


and the .deb files are never created. Why would it stop after not finding 'readme'?  :???:  I'm really confused....

---

### Post by jkndrkn on 2005-05-23
I'm not sure if this helps, but it seems that the wiki I pointed you to is specific for ndiswrapper-1.1.tar.gz.

Perhaps your version of ndiswrapper is subtly different, causing you to be unable to use the wiki.

Sorry, but I'm not sure if I can help you any further.

Hope you get your 'wrapper up and running. Until I found and followed the wiki, it caused me quite a headache.

---

### Post by avatar_58 on 2005-05-23
Yes! It works!  \\:D/ 

I had to rename the readme file to README (odd isn't it?) and then according to another faq I had to change the arch type from i386 to amd64 in the control files, and FINALLY I had to run it with a make -i to skip some minor blocks.

Then using iwconfig I connected and was browsing the internet from ubuntu. 

 :-P

---

