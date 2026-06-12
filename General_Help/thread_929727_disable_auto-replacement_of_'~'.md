---
title: "disable auto-replacement of '~'"
date: 2008-09-25
forum: General Help
---

### Post by ycrane on 2008-09-25
with its absolute path, like '/home/usrname', when typing ~/, following with a 'TAB' key. The auto replacement seems a nice feature on Ubuntu (8.04), but I really prefer to see a shorter path.

Thanks!

---

### Post by Pelham123 on 2008-09-25
You need to edit the following file:

/etc/bash_completion

You will need to use sudo, please make a backup of file first. Open file and look for this section...line 336 or close ;)

```
# This function expands tildes in pathnames
#
_expand()
{
	# FIXME: Why was this here?
	# [ "$cur" != "${cur%\\}" ] && cur="$cur\\"

	# expand ~username type directory specifications
	if [[ "$cur" == \~*/* ]]; then
		eval cur=$cur
	elif [[ "$cur" == \~* ]]; then
		cur=${cur#\~}
		COMPREPLY=( $( compgen -P '~' -u $cur ) )
		return ${#COMPREPLY[@]}
	fi
}

```

Edit it out. 
Save. 
Logout. 
Done.

---

