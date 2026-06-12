---
title: "trying to install armagedtronAD"
date: 2008-09-20
forum: General Help
---

### Post by jmd9qs on 2008-09-20
hey,

i downloaded and am trying to isntall armagedtronAD {which i gather is like Tron, but cooler cause its linux :) }. everything goes cool until i run:
```

make install
```

at which point:
```

 make install
Making install in src
make[1]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src'
Making install in first
make[2]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/first'
make[3]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/first'
make -C ../../ install-first
make[4]: Entering directory `/media/disk/armagetronad-0.2.8.2.1'
test -x /usr/local/bin/armagetronad-uninstall && /usr/local/bin/armagetronad-uninstall || true
make[4]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/first'
make[2]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/first'
Making install in doc
make[2]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/doc'
Making install in net
make[3]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/doc/net'
make[4]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/doc/net'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/games/armagetronad/html/net" || mkdir -p -- "/usr/local/share/doc/games/armagetronad/html/net"
 /usr/bin/install -c -m 644 'index.html' '/usr/local/share/doc/games/armagetronad/html/net/index.html'
/usr/bin/install: cannot remove `/usr/local/share/doc/games/armagetronad/html/net/index.html': Permission denied
 /usr/bin/install -c -m 644 'lower.html' '/usr/local/share/doc/games/armagetronad/html/net/lower.html'
/usr/bin/install: cannot remove `/usr/local/share/doc/games/armagetronad/html/net/lower.html': Permission denied
 /usr/bin/install -c -m 644 'middle.html' '/usr/local/share/doc/games/armagetronad/html/net/middle.html'
/usr/bin/install: cannot remove `/usr/local/share/doc/games/armagetronad/html/net/middle.html': Permission denied
 /usr/bin/install -c -m 644 'upper.html' '/usr/local/share/doc/games/armagetronad/html/net/upper.html'
/usr/bin/install: cannot remove `/usr/local/share/doc/games/armagetronad/html/net/upper.html': Permission denied
make[4]: *** [install-htmlDATA] Error 1
make[4]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/doc/net'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/doc/net'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/doc'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src'
make: *** [install-recursive] Error 1
```

when i try w/ sudo:

```
sudo make install
Making install in src
make[1]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src'
Making install in first
make[2]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/first'
make[3]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/first'
make -C ../../ install-first
make[4]: Entering directory `/media/disk/armagetronad-0.2.8.2.1'
test -x /usr/local/bin/armagetronad-uninstall && /usr/local/bin/armagetronad-uninstall || true
make[4]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/first'
make[2]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/first'
Making install in doc
make[2]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/doc'
Making install in net
make[3]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/doc/net'
make[4]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/doc/net'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/games/armagetronad/html/net" || mkdir -p -- "/usr/local/share/doc/games/armagetronad/html/net"
 /usr/bin/install -c -m 644 'index.html' '/usr/local/share/doc/games/armagetronad/html/net/index.html'
 /usr/bin/install -c -m 644 'lower.html' '/usr/local/share/doc/games/armagetronad/html/net/lower.html'
 /usr/bin/install -c -m 644 'middle.html' '/usr/local/share/doc/games/armagetronad/html/net/middle.html'
 /usr/bin/install -c -m 644 'upper.html' '/usr/local/share/doc/games/armagetronad/html/net/upper.html'
make[4]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/doc/net'
make[3]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/doc/net'
make[3]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/doc'
make[4]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/doc'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/games/armagetronad/html" || mkdir -p -- "/usr/local/share/doc/games/armagetronad/html"
 /usr/bin/install -c -m 644 'bugs.html' '/usr/local/share/doc/games/armagetronad/html/bugs.html'
 /usr/bin/install -c -m 644 'changelog.html' '/usr/local/share/doc/games/armagetronad/html/changelog.html'
 /usr/bin/install -c -m 644 'commands.html' '/usr/local/share/doc/games/armagetronad/html/commands.html'
 /usr/bin/install -c -m 644 'compile.html' '/usr/local/share/doc/games/armagetronad/html/compile.html'
 /usr/bin/install -c -m 644 'config.html' '/usr/local/share/doc/games/armagetronad/html/config.html'
 /usr/bin/install -c -m 644 'faq.html' '/usr/local/share/doc/games/armagetronad/html/faq.html'
 /usr/bin/install -c -m 644 'index.html' '/usr/local/share/doc/games/armagetronad/html/index.html'
 /usr/bin/install -c -m 644 'install_linux.html' '/usr/local/share/doc/games/armagetronad/html/install_linux.html'
 /usr/bin/install -c -m 644 'install_macosx.html' '/usr/local/share/doc/games/armagetronad/html/install_macosx.html'
 /usr/bin/install -c -m 644 'install_result.html' '/usr/local/share/doc/games/armagetronad/html/install_result.html'
 /usr/bin/install -c -m 644 'install_windows.html' '/usr/local/share/doc/games/armagetronad/html/install_windows.html'
 /usr/bin/install -c -m 644 'network.html' '/usr/local/share/doc/games/armagetronad/html/network.html'
 /usr/bin/install -c -m 644 'readme_macosx.html' '/usr/local/share/doc/games/armagetronad/html/readme_macosx.html'
 /usr/bin/install -c -m 644 'todo.html' '/usr/local/share/doc/games/armagetronad/html/todo.html'
 /usr/bin/install -c -m 644 'versions.html' '/usr/local/share/doc/games/armagetronad/html/versions.html'
make[4]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/doc'
make[3]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/doc'
make[2]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/doc'
Making install in thirdparty
make[2]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/thirdparty'
Making install in particles
make[3]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/thirdparty/particles'
make[4]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/thirdparty/particles'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/thirdparty/particles'
make[3]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/thirdparty/particles'
make[3]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/thirdparty'
make[4]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src/thirdparty'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/thirdparty'
make[3]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/thirdparty'
make[2]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src/thirdparty'
make[2]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src'
make[3]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'armagetronad_main' '/usr/local/bin/armagetronad_main'
make[3]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src'
make[2]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src'
make[1]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/src'
Making install in resource
make[1]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/resource'
make[2]: Entering directory `/media/disk/armagetronad-0.2.8.2.1/resource'
make[2]: Nothing to be done for `install-exec-am'.
if test -d included; then\
		ln -sf included linked_included.install;\
	else\
		ln -sf ./included linked_included.install;\
	fi
ln: creating symbolic link `linked_included.install': Operation not permitted
make[2]: *** [linked_included.install] Error 1
make[2]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/resource'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/media/disk/armagetronad-0.2.8.2.1/resource'
make: *** [install-recursive] Error 1
jmd9qs@jmd9qs-desktop:/media/disk/armagetronad-0.2.8.2.1$ 
```

i'm kinda a newbie, so i'm not sure what to try at this juncture...

any suggestions?

---

### Post by jmd9qs on 2008-09-22
bump bump bump...

---

