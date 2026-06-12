---
title: "Run script when specific e-SATA hdd is mounted"
date: 2011-08-16
forum: Hardware
---

### Post by kasi1999999 on 2011-08-16
Hi all,
I can not find solution, how to run script, when I mount my e-SATA harddrive. I found solution, when I use disk connected via USB, but nothing consider SATA devices. I would like to use my disk for backuping. Thanks for answers.

---

### Post by dleinhaeuser on 2011-08-23
Your best bet is udev in this case.
I hade the same issue and used a udev rule that would run a certain script whenever a partition was added to the system, whose volume label matched a certain pattern.
In this case I chose to store the actual backup-script on the external drive as well.
So there are two parts in this case, a script on the external HDD.
For example:
```

#!/bin/bash
SOURCE_DIR=".../"
BACKUP_DIR=".../"
rdiff-backup --print-statistics "$SOURCE_DIR" "$PWD/$BACKUP_DIR"

```

The second part is a script that is called by udev, when the rule matches, mounts the partition, runs the backup-script, if it exists, umounts the drive and sends a report via e-mail.
```

#!/bin/bash
function canonical () {
	if pushd -- "$(dirname -- "$1")" >/dev/null; then
		echo "$PWD/$(basename "$1")"
		popd >/dev/null
	fi
	exit $?
}

RULES_NAME="/etc/udev/rules.d/hdd-backup.rules"

case "$1" in
--enable)
	exec udevadm control --property=HDD_BACKUP_DISABLE=no
	;;
--disable)
	exec udevadm control --property=HDD_BACKUP_DISABLE=yes
	;;
--install)
	EMAIL="${2:-root}"
	BACKUP_SCRIPT="${3:-backup-script}"
	LABEL_PATTERN="${4:-backup_*}"
	SCRIPT_NAME="$(canonical "$0")" ||*exit $?
	exec cat >"$RULES_NAME" <<-EOF
		SUBSYSTEM=="block", ACTION=="add", ENV{HDD_BACKUP_DISABLE}!="yes", ENV{ID_FS_LABEL}=="$LABEL_PATTERN", RUN+="$SCRIPT_NAME --run-backup '$EMAIL' '$BACKUP_SCRIPT' &"
	EOF
	;;
--uninstall)
	exec rm "$RULES_NAME"
	;;
--run-backup)
	EMAIL="$2"
	BACKUP_SCRIPT="$3"
	[ -n "$EMAIL" ] && [ -n "$DEVNAME" ] && [ -n "$BACKUP_SCRIPT" ] || exit 1
	;;
*)
	cat <<-EOF
		Options:
		--enable
		    Enable run-backup.
		--disable
		    Temporarily disable run-backup.
		--install [EMAIL] [PATTERN] [SCRIPT]
		    Install udev rule.
		    If a drive with a partition whose label matches
		    PATTERN (default: backup_*) is inserted and contains
		    an executable file named SCRIPT (default: backup-script),
		    then it will be executed and the result mailed to
		    EMAIL (default: root).
		    Afterwards the drive will be unmounted again.
		--uninstall
		    Remove the udev rule.
	EOF
	exit 1
	;;
esac

TEMP="$(mktemp -d /tmp/run-backup.XXX 2>&1)" || {
	ERR="$?"
	mail -s "Backup failed!" "$EMAIL" <<-EOF
		mktemp: $TEMP
	EOF
	exit $ERR
}

function mountAndRun () {
	MOUNTPOINT="$1"
	RESULT=0
	if mkdir -p "$MOUNTPOINT"; then
		if mount "$DEVNAME" "$MOUNTPOINT"; then
			if [ -x "$MOUNTPOINT/$BACKUP_SCRIPT" ]; then
				if pushd "$MOUNTPOINT" >/dev/null; then
					if "./$BACKUP_SCRIPT"; then
						sync
					else
						RESULT="$?"
					fi
					popd >/dev/null
				else
					RESULT="$?"
				fi
			else
				echo "$BACKUP_SCRIPT not found or not executable." >&2
				RESULT=1
			fi
			umount "$MOUNTPOINT"
			[ "$RESULT" == "0" ] && hdparm -Y "$DEVNAME" >/dev/null
		else
			RESULT="$?"
		fi
		rmdir "$MOUNTPOINT"
	else
		RESULT="$?"
	fi
	
	return "$RESULT"
}

if mountAndRun "$TEMP/mnt" >"$TEMP/output" 2>&1; then
	SUBJECT="Backup successful."
else
	SUBJECT="Backup failed!"
fi

mail -s "hdd-backup: $SUBJECT" "$EMAIL" < "$TEMP/output"

rm "$TEMP/output" && rmdir "$TEMP"

```

DISCLAIMER:
Use this script at your own risk.
It seems to work on my server, but on yours it might delete important files and play Rebecca Black on an endless loop.

---

