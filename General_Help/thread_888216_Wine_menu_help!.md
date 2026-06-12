---
title: "Wine menu help!"
date: 2008-08-12
forum: General Help
---

### Post by Tibco on 2008-08-12
I accidentally messed up my wine, when installing a windows program and so i decided to reinstall it. I uninstalled it through add/remove programs, then deleted .wine folder in my home directory. I then noticed that i still had a Wine menu under applications, so i went to edit menu, and got rid of the programs sub menu, so that Wine wouldn't show up under applications. When i reinstall wine, i don't get that programs menu back (hence, i cant use notepad unless i go into my cdrive>windows>and then launch notepad.exe). Is there any way i can get it back?

---

### Post by mc4man on 2008-08-12
What's here should work
[http://ubuntuforums.org/showthread.php?t=650738](http://ubuntuforums.org/showthread.php?t=650738)
Ex. I delete wine menu

( .config/menus/applications.menu

```

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Other</Name>
		<Include>
			<Filename>displayconfig-gtk.desktop</Filename>
		</Include>
		<AppDir>/home/doug/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>System</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Include>
			<Filename>gconf-editor.desktop</Filename>
		</Include>
		<AppDir>/home/doug/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>wine-wine</Name>
		<Menu>
			<Name>wine-Programs</Name>
			<Menu>
				<Name>wine-Programs-ImgBurn</Name>
				<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
			</Menu>
		</Menu>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>
```

Remove what's in red and then backspace 1 line (1 space between lines

---

### Post by Tibco on 2008-08-13
works perfectly thanks!

---

