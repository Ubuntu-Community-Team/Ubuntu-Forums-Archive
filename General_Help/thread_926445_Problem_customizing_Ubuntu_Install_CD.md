---
title: "Problem customizing Ubuntu Install CD"
date: 2008-09-21
forum: General Help
---

### Post by ymenager on 2008-09-21
I'm trying to customize the ubuntu live-cd following the instructions on the wiki, but i've ran into some weird trouble.

I run the following scripts to insert my own key in the ubuntu-keyring, and update all the md5s and such, so that i may start adding new packages in an new extras repository on the CD.

However, the iso generated from that process tries to configure and start a PPPoE connection, and then off course fails since there isn't one.

Any idea what's causing that happen and how to fix it ?

--- Script 1

cd ../
mkdir -p _build/keyring
cd _build/keyring
sudo apt-get source ubuntu-keyring
UNAME=`whoami`
sudo chown -R $UNAME:$UNAME ubuntu-keyring*
rm ubuntu-keyring_2008.03.04.dsc
rm ubuntu-keyring_2008.03.04.tar.gz
cd ubuntu-keyring-2008.03.04/keyrings
gpg --export FBB75451 437D05B5 0E484B75 > ubuntu-archive-keyring.gpg
cd ..
rm md5sums.txt
md5sum keyrings/ubuntu-archive-keyring.gpg >md5sums.txt
sudo dpkg-buildpackage -rfakeroot -m"My Key" -k0E484B75
sudo chown -R $UNAME:$UNAME ../*

----- Script 2 

#!/bin/bash

# go to build dir
cd ../_build

mkdir -p mnt
sudo mount -o loop /var/storage/Software/ubuntu-8.04.1-server-i386.iso mnt
rm -rf image
mkdir -p image
rsync -qav mnt/ image/
sudo chmod -R u+w image
sudo umount mnt
rm -r mnt

#cp -R extra-repos image
cp keyring/ubuntu-keyring*deb image/pool/main/u/ubuntu-keyring
mkdir -p indices apt-ftparchive
cd indices
for SUFFIX in extra.main main main.debian-installer restricted restricted.debian-installer; do
  wget http://archive.ubuntu.com/ubuntu/indices/override.hardy.$SUFFIX
done
cd ..
sed -e "s|\/opt\/cd-image|`pwd`\/image|g" -e "s|\/opt\/indices|`pwd`\/indices|g" <../src//apt-ftparchive-deb.conf >apt-ftparchive/apt-ftparchive-deb.conf
sed -e "s|\/opt\/cd-image|`pwd`\/image|g" -e "s|\/opt\/indices|`pwd`\/indices|g" <../src//apt-ftparchive-udeb.conf >apt-ftparchive/apt-ftparchive-udeb.conf
#sed -e "s|\/opt\/cd-image|`pwd`\/image|g" -e "s|\/opt\/indices|`pwd`\/indices|g" <../src//apt-ftparchive-extras.conf >apt-ftparchive/apt-ftparchive-extras.conf
cd image
apt-ftparchive -c ../../src/release.conf generate ../apt-ftparchive/apt-ftparchive-deb.conf
apt-ftparchive -c ../../src/release.conf generate ../apt-ftparchive/apt-ftparchive-udeb.conf
#apt-ftparchive -c ../../src/release.conf generate ../apt-ftparchive/apt-ftparchive-extras.conf
apt-ftparchive -c ../../src/release.conf release dists/hardy > dists/hardy/Release
rm dists/hardy/Release.gpg
gpg --default-key "0E484B75" --output dists/hardy/Release.gpg -ba dists/hardy/Release

#cp ../src/test.seed image/preseed
#sed s/ubuntu-server.seed/test.seed/ <image/isolinux/isolinux.cfg >isolinux.cfg
#mv isolinux.cfg image/isolinux/
rm md5sum.txt
find -type f ! -name md5sum.txt ! -path '*/isolinux/*' -print0 | xargs -0 md5sum > md5sum.txt
cd ..
mkisofs -r -V "Custom Ubuntu Install CD" \
            -cache-inodes \
            -J -l -b isolinux/isolinux.bin \
            -c isolinux/boot.cat -no-emul-boot \
            -boot-load-size 4 -boot-info-table \
            -o custom.iso image

---

