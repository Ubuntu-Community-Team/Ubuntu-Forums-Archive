---
title: "Use live CD Image via NFS"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by TooTechy on 2009-03-05
I hope this is the correct location for this post but I am new to these forums.

The aim for this current project is for a remote PC (in the garage) disconnected from the house to PXE boot, via tftp and NFS, an expanded copy (ie. all the CD files in an exported directory) of the ubuntu 8.10 desktop i386 CDROM Live image and then NFS mount a separate RW partition to enable the persistent storage of data without modifying the CDROM copy (makes for easier updates).

The machine will act as an autonomous remote backup facility using rsync. It will have some disk with encrypted storage to store copies of all our files but will not have the means to access the data unless connected to this network as it will not boot and not have the keys. Thus if it is stolen, our data is safe. If our house is lost, all we need are the keys to the FS crypto to salvage the data using :Danother machine.

Firstly, all the boot process is working. But I had to modify the initrd contained on the CDROM.

I have to congratulate the writers of the casper scripts. To get as far as I did without having to change more than a few lines was very cool. The scripts are brilliant. But to enable the NFS RW root partition I had to add a few lines. 

The question is... Is there a better way of achieving this without modifying the initrd?

In the init script I added the following (nfsrootrw)

        cryptopts=*)
                cryptopts="${x#cryptopts=}"
                ;;
        nfsrootrw=*)
                NFSROOTRW="${x#nfsrootrw=}"
                ;;
        nfsroot=*)
                NFSROOT="${x#nfsroot=}"
                ;;
 
In Casper I added the following (NFSROOTRW)

... if [ -n "${PERSISTENT}" ]; then
        cowprobe=$(find_cow_device "${root_persistence}")
        if [ -b "${cowprobe}" ]; then
            cowdevice=${cowprobe}
            cow_fstype=$(get_fstype "${cowprobe}")
            cow_mountopt="rw,noatime"
        else
            [ "$quiet" != "y" ] && log_warning_msg "Unable to find the persistent medium"
        fi
    fi

    if [ -n "$NFSROOTRW" ] ; then
        [ "$quiet" != "y" ] && log_warning_msg "Looking for NFS Persistent root"
        configure_networking
        #IPV4ADDR=192.168.0.152
        cow_fstype=nfs
        cowdevice="$NFSROOTRW"/"$IPV4ADDR"
        cow_mountopt=rw,nolock
    fi

All this could be alleviated if the mountroot function checked for a mountroot.local script on the ROOT medium. The mountroot.local script could then check and setup and mount what it needed to to continue.

Any Thoughts?

---

