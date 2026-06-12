---
title: "need little hint... about Menu Editor"
date: 2008-09-06
forum: General Help
---

### Post by ichundu on 2008-09-06
hi everyone,
i had the wine menu in the top of all other menus (inside Applications menu), and i dragged it on the bottom of the list under Applications menu (in the "Main Menu" editor), just where it was before deleting it involuntary, but it finished inside the Universal Access menu. then i opened application.menu file where i tried to take this action back, and well, i did that, but in the Universal Access menu remained an item called "wine-wine". i had probably messed something up in the "application.menu" file. i did purposely undo these actions and now i'm back where the wine menu was inside Universal Access menu.
now i need your help to make this without causing further mistakes to the "application.menu" file. i'm posting this file here hoping that anyone could tell where me to move the responsible part of text in the right place (i'm so sorry for having to post this long message).
thanks for your time !

PS: if you find it easier, i'm attaching the file too (at the end of the post), so anyone could do the changes: 
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Move>
		<Old>wine-wine</Old>
		<New>Universal Access/wine-wine</New>
	</Move>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Other</Name>
		<DirectoryDir>/home/lindi/.local/share/desktop-directories</DirectoryDir>
		<AppDir>/home/lindi/.local/share/applications</AppDir>
		<Include>
			<Filename>nautilus-autorun-software.desktop</Filename>
		</Include>
		<Include>
			<Filename>seahorse-pgp-encrypted.desktop</Filename>
		</Include>
		<Include>
			<Filename>gnome-font-viewer.desktop</Filename>
		</Include>
		<Include>
			<Filename>seahorse-pgp-keys.desktop</Filename>
		</Include>
		<Include>
			<Filename>gmenu-simple-editor.desktop</Filename>
		</Include>
		<Include>
			<Filename>nautilus-folder-handler.desktop</Filename>
		</Include>
		<Include>
			<Filename>displayconfig-gtk.desktop</Filename>
		</Include>
		<Include>
			<Filename>sun-java6-java.desktop</Filename>
		</Include>
		<Include>
			<Filename>gnome-theme-installer.desktop</Filename>
		</Include>
		<Include>
			<Filename>seahorse-pgp-signature.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Development</Name>
		<DirectoryDir>/home/lindi/.local/share/desktop-directories</DirectoryDir>
		<AppDir>/home/lindi/.local/share/applications</AppDir>
		<Include>
			<Filename>python2.5.desktop</Filename>
		</Include>
		<Include>
			<Filename>bug-buddy.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Universal Access</Name>
		<DirectoryDir>/home/lindi/.local/share/desktop-directories</DirectoryDir>
		<AppDir>/home/lindi/.local/share/applications</AppDir>
		<Include>
			<Filename>orca.desktop</Filename>
		</Include>
		<Menu>
			<Name>wine-wine</Name>
		</Menu>
	</Menu>
	<Menu>
		<Name>System</Name>
		<DirectoryDir>/home/lindi/.local/share/desktop-directories</DirectoryDir>
		<AppDir>/home/lindi/.local/share/applications</AppDir>
		<Include>
			<Filename>gconf-editor.desktop</Filename>
		</Include>
		<Include>
			<Filename>gfloppy.desktop</Filename>
		</Include>
		<Include>
			<Filename>gdebi.desktop</Filename>
		</Include>
		<Include>
			<Filename>gdmflexiserver.desktop</Filename>
		</Include>
		<Include>
			<Filename>gdmflexiserver-xnest.desktop</Filename>
		</Include>
		<Include>
			<Filename>apport-gtk-mime.desktop</Filename>
		</Include>
		<Include>
			<Filename>gksu.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Accessories</Name>
		<AppDir>/home/lindi/.local/share/applications</AppDir>
		<Include>
			<Filename>file-roller.desktop</Filename>
		</Include>
		<Include>
			<Filename>bluetooth-analyzer.desktop</Filename>
		</Include>
		<Include>
			<Filename>nautilus.desktop</Filename>
		</Include>
		<Include>
			<Filename>gnome-panel.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Graphics</Name>
		<AppDir>/home/lindi/.local/share/applications</AppDir>
		<Include>
			<Filename>evince.desktop</Filename>
		</Include>
		<Include>
			<Filename>f-spot-import.desktop</Filename>
		</Include>
		<Include>
			<Filename>f-spot-view.desktop</Filename>
		</Include>
		<Include>
			<Filename>eog.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Internet</Name>
		<AppDir>/home/lindi/.local/share/applications</AppDir>
		<Include>
			<Filename>vinagre-file.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Office</Name>
		<AppDir>/home/lindi/.local/share/applications</AppDir>
		<Include>
			<Filename>evolution-2.2.desktop</Filename>
		</Include>
		<Include>
			<Filename>ooo-template.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Multimedia</Name>
		<AppDir>/home/lindi/.local/share/applications</AppDir>
		<Include>
			<Filename>totem-gstreamer.desktop</Filename>
		</Include>
		<Include>
			<Filename>reclevel.desktop</Filename>
		</Include>
		<Include>
			<Filename>gnome-volume-control.desktop</Filename>
		</Include>
		<Include>
			<Filename>vumeter.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>wine-wine</Name>
	</Menu>
	<DefaultLayout inline="false"/>
	<Menu>
```

---

### Post by ichundu on 2008-09-07
maybe anyone (who has wine on the applications menu) can compare my file to his own (BTW, this is the path: /home/.config/menus/applications.menu) and tell me where to place the part of the text that should do the work. it should look like this (near the end of the file):
```
<Menu>
                <Name>wine-wine</Name>
        </Menu>

```
or
```
<Menu>
                <Name>wine-wine</Name>
                <Menu>
                        <Name>wine-Programs</Name>
                        <Menu>
                                <Name>wine-Programs-AutoHotkey</Name>
                                <DirectoryDir>/home/user/.local/share/desktop-directories</DirectoryDir>
                        </Menu>
                </Menu>
        </Menu>

```
plz:)

---

### Post by ichundu on 2008-09-07
:guitar: ok i did that, i got Wine off Universal Access menu. now i'm wondering if you could tell me this last thing, want to move it to the end of the drop down list, in the applications menu.
come on... should be easy :)

---

