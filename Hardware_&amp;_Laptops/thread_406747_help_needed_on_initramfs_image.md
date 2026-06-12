---
title: "help needed on initramfs image"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by saikumar_divvela on 2007-04-11
Hello All,

I have a problem partitioning of hard disk through initramfs image.
Through bootable cd and  using loadlin tool i am loading vmlinuz(2.6.17) and initramfs image in memory.
I customized the initramfs image such that its init script calls my script which will partition the hard disk.  I am having problem at this stage

the following error is thrown
unable to load /dev/sda 

the init script is 

#!/bin/sh

mkdir /sys
mkdir /proc
mkdir /tmp

mkdir -p /var/lock
mount -t sysfs none /sys -onodev,noexec,nosuid
mount -t proc none /proc -onodev,noexec,nosuid

echo "I am in init script"
sleep 5

# Note that this only becomes /dev on the real filesystem if udev's scripts
# are used; which they will be, but it's worth pointing out
tmpfs_size="10M"
mount -t tmpfs -o size=$tmpfs_size,mode=0755 udev /dev
> /dev/.initramfs-tools
mkdir /dev/.initramfs
mknod /dev/console c 5 1
mknod /dev/null c 1 3

# Export the dpkg architecture
export DPKG_ARCH=
. /conf/arch.conf

# Export it for root hardcoding
export ROOT=

# Bring in the main config
. /conf/initramfs.conf
for i in conf/conf.d/*; do
        [ -f ${i} ] && . ${i}
done
. /scripts/functions

call() {
        . "$@"
}

# Parse command line options
export PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/bin2:/usr/lib:/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib:/lib
export break=
export init=/sbin/init
export quiet=n
export readonly=y
export rootmnt=/root
export debug=
export cryptopts=${CRYPTOPTS}



for x in $(cat /proc/cmdline); do
        case $x in
        init=*)
                init=${x#init=}
                ;;
        root=*)
                ROOT=${x#root=}
                case $ROOT in
                LABEL=*)
                        ROOT="/dev/disk/by-label/${ROOT#LABEL=}"
                        ;;
                UUID=*)
                        ROOT="/dev/disk/by-uuid/${ROOT#UUID=}"
                        ;;
                esac
                ;;
        rootflags=*)
                ROOTFLAGS="-o ${x#rootflags=}"
                ;;
        cryptopts=*)
                cryptopts="${x#cryptopts=}"
                ;;
        nfsroot=*)
                NFSROOT="${x#nfsroot=}"
                ;;
        nfsopts=*)
                NFSOPTS="-o ${x#nfsopts=}"
                ;;
        boot=*)
                BOOT=${x#boot=}
                ;;
        resume=*)
                RESUME=${x#resume=}
                ;;
        noresume)
                NORESUME=y
                ;;
        quiet)
                quiet=y
                ;;
        ro)
                readonly=y
                ;;
        rw)
                readonly=n
                ;;
        debug)
                debug=y
                exec >/tmp/initramfs.debug 2>&1
                set -x
                ;;
        break=*)
                break=${x#break=}
                ;;
        break)
                break=premount
                ;;
        esac
done

if [ -z ${NORESUME} ]; then
        export resume=${RESUME}
fi

depmod -a
maybe_break top

# Don't do log messages here to avoid confusing usplash
run_scripts /scripts/init-top

maybe_break modules
log_begin_msg "Loading essential drivers..."
load_modules
log_end_msg

maybe_break premount

echo "printing configurations"
sleep 10
echo "quiet=$quiet"
echo "root=$ROOT"
echo "rootmnt=$rootmnt"
sleep 10

echo "running init-premount scripts"
[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/init-premount"
run_scripts /scripts/init-premount
[ "$quiet" != "y" ] && log_end_msg

sleep 10

echo "calling the partition script"

**call /scripts/script**  # This is the partition script i am calling[/B]

maybe_break mount
log_begin_msg "Mounting root file system..."
. /scripts/${BOOT}
parse_numeric ${ROOT}
mountroot
log_end_msg

maybe_break bottom
[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/init-bottom"
run_scripts /scripts/init-bottom
[ "$quiet" != "y" ] && log_end_msg


# Move virtual filesystems over to the real filesystem
mount -n -o move /sys ${rootmnt}/sys
mount -n -o move /proc ${rootmnt}/proc

while [ ! -x ${rootmnt}${init} ]; do
        panic "Target filesystem doesn't have ${init}"
done

# Confuses /etc/init.d/rc
if [ -n ${debug} ]; then
        unset debug
fi

# Chain to real filesystem
maybe_break init
exec run-init ${rootmnt} ${init} "$@" <${rootmnt}/dev/console >${rootmnt}/dev/console

####end of init script

the script /scripts/script is

#!/bin/sh -x

mount -n -t ramfs ramfs /tmp
mount -n -t proc proc /proc
mount -n -t sysfs sysfs /sys

**fdisk /devfs/discs/disc0/disc <<'EOP'**  
n
p
2

+1666M
n
p
3

+100M
n
e


n

+2088M
t
5
82
n

+4096M
n


p
w
EOP

sleep 5
#reboot -f

In the above script fdisk is failing with error "unable to open /dev/sda"
I think by the time i call /scripts/script all the modules are loaded and fdisk should recognize the hard disk sda (scsci).
I have no clue why this error is happening.
If any body knows about this  please help me

Thanks 
Sa

---

