---
title: "Error at the installation intel-linux-installer  under kubuntu 13.10 64 bits"
date: 2014-01-14
forum: Hardware
---

### Post by michel.morisot on 2014-01-14
Hello,

Error at the installation intel-linux-installer under kubuntu 13.10 64 bits


michel@micmormobile:~$ sudo intel-linux-graphics-installer 1.0.3
[sudo] password for michel: 
Sorry, try again.
[sudo] password for michel: 

(intel-linux-graphics-installer:4753): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
diagnostics-view.c/new_diagnostic: Adding diagnostic for Checking if Intel graphics card available...
diagnostics-view.c/new_diagnostic: Adding diagnostic for Retrieving information from 01.org...
diagnostics-view.c/new_diagnostic: Adding diagnostic for Checking distribution...
diagnostics-view.c/new_diagnostic: Adding diagnostic for Checking kernel version...
diagnostics-view.c/new_diagnostic: Adding diagnostic for Checking available repositories...
diagnostics-view.c/new_diagnostic: Adding diagnostic for Checking package manager status...
No LSB modules are available.
polkit: Fetching org.01.linuxgraphics.installer permissions...
diagnostics-view.c/diagnostics_view_start: Running diagnostic Checking if Intel graphics card available...
diagnostics-view.c/diagnostics_view_start: Running diagnostic Retrieving information from 01.org...
{
  errors: (nil)
  sources: []
  keys: []
  docs: []
  INSTALL: []
  install: []
  upgrade: []
}
diagnostics-view.c/diagnostics_view_start: Running diagnostic Checking distribution...
&#62811; package_manager_is_distro_supported
&#62811; Configuration : Loading …  [   0 % ] &#9202;
{
  errors: (nil)
  sources: []
  keys: []
  docs: []
  INSTALL: []
  install: []
  upgrade: []
}
&#62811; package_manager_is_distro_supported
&#62811; Configuration : Loaded  [  80 % ] &#9202;
&#62811; package_manager_is_distro_supported
&#62811; Configuration : Testing …  [  80 % ] &#9202;                                                                                                                                                                                                                                      
&#62811; package_manager_is_distro_supported                                                                                                                                                                                                                                         
&#62811; Configuration : Complete  [  ] &#9702;                                                                                                                                                                                                                                            
main-window.c/on_diagnostics_finished: Diagnostics finished with an error                                                                                                                                                                                                      
                                                                                     



Checking if Intel graphics card available... OK
Retrieving information from 01.org... OK
Checking distribution... Failed

---

### Post by michel.morisot on 2014-01-14
The problem was identified on [url] https://01.org/linuxgraphics/comment/508 # comment-508 [/ url]. It is located in a configuration file on the server intel, useful for the installer.

---

