---
title: "[SOLVED] symlink problem with dirs created by gvfs"
date: 2008-10-20
forum: General Help
---

### Post by asipi on 2008-10-20
Hi,

I made a script to make symbolic links for mounting smb share via gvfs based on the gtk-bookmarks (idea from.

I would like to make symlinks in my $HOME for each share, but if the filename created for the share by gvfs in the ~/.gvfs directory consists spaces (of course it does :( ), ln refuses to make the symlinks, it says blabla is not a directory.

As I realized ln takes the argument given to it and divides it at the spaces, so it gets to much argument.

If I make it by hand, it works well (I used backslashes to indicates the spaces). I used sed to place backslashes in the dirname before the spaces but it wasn't successfull.

here is the script:
```
LIST=`grep smb:// ~/.gtk-bookmarks|cut -d ' ' -f 1`
for ITEM in $LIST ; do
	BOOKMARK_NAME=`grep $ITEM ~/.gtk-bookmarks|cut -d ' ' -f 2`
	gvfs-mount $ITEM
	SHARE_NAME=`echo $ITEM|cut -d '/' -f 4`
	ITEM_MPOINT=`ls $HOME/.gvfs| grep $SHARE_NAME | sed s/' '/'\\ '/g`
	echo "$ITEM - $SHARE_NAME - $ITEM_MPOINT"
	# create the link if does not exist
	if [ ! -e $HOME/$BOOKMARK_NAME ] ; then
		ln -v -s -T "$HOME/.gvfs/$ITEM_MPOINT" "$HOME/$BOOKMARK_NAME"
	fi
done
```

So I want ln to handle the given operand as one operand even if it holds spaces.

Any help would be appreciated.

*[COLOR="Blue"]**SOLVED**: Need to put the operand of ln into quatation marks.[/COLOR]*

---

