---
title: "cannot install modules via CPAN"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by asad747 on 2009-02-10
Dear all I am trying to install Perl modules via CPAN, but i am getting errors everytime.

> Manifying ../blib/man3/XML::RSS.3pm
make[1]: Leaving directory `/usr/bin/perl -MCPAN -e 'install "Term::ShellUI"'/SHLOMIF-plhPBS/XML-RSS-1.43'
  SHLOMIF/XML-RSS-1.43.tar.gz
  /usr/bin/make -- OK
Running make test
make[1]: Entering directory `/usr/bin/perl -MCPAN -e 'install "Term::ShellUI"'/SHLOMIF-plhPBS/XML-RSS-1.43'
make[1]: Leaving directory `/usr/bin/perl -MCPAN -e 'install "Term::ShellUI"'/SHLOMIF-plhPBS/XML-RSS-1.43'
make[1]: Entering directory `/usr/bin/perl -MCPAN -e 'install "Term::ShellUI"'/SHLOMIF-plhPBS/XML-RSS-1.43'
/usr/bin/perl "-MTest::Manifest" "-e" "run_t_manifest(0, '../blib/lib', '../blib/arch')"
Can't locate Test/Manifest.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .).
BEGIN failed--compilation aborted.
make[1]: *** [test_dynamic] Error 2
make[1]: Leaving directory `/usr/bin/perl -MCPAN -e 'install "Term::ShellUI"'/SHLOMIF-plhPBS/XML-RSS-1.43'
make: *** [subdirs-test] Error 2
  SHLOMIF/XML-RSS-1.43.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports SHLOMIF/XML-RSS-1.43.tar.gz
Running make install
  make test had returned bad status, won't install without force
Failed during this command:
 SHLOMIF/XML-RSS-1.43.tar.gz                  : make_test NO


**Here is my CPAN Configuration**

> cpan[2]> o conf
$CPAN::Config options from '/etc/perl/CPAN/Config.pm':
    commit             [Commit changes to disk]
    defaults           [Reload defaults from disk]
    help               [Short help about 'o conf' usage]
    init               [Interactive setting of all options]

    applypatch         []
    auto_commit        [1]
    build_cache        [100]
    build_dir          [/usr/bin/perl -MCPAN -e 'install "Term::ShellUI"']
    build_dir_reuse    [0]
    build_requires_install_policy [ask/yes]
    bzip2              [/bin/bzip2]
    cache_metadata     [1]
    check_sigs         [0]
    colorize_debug     undef
    colorize_output    [0]
    colorize_print     undef
    colorize_warn      undef
    commandnumber_in_prompt [1]
    commands_quote     undef
    cpan_home          [/usr/bin/perl -MCPAN -e 'install "XML::SemanticDiff"']
    curl               []
    dontload_hash      undef
    dontload_list      undef
    ftp                [/usr/bin/ftp]
    ftp_passive        [1]
    ftp_proxy          []
    getcwd             [cwd]
    gpg                [/usr/bin/gpg]
    gzip               [/bin/gzip]
    histfile           [/usr/bin/perl -MCPAN -e 'install "XML::SemanticDiff"'/histfile]
    histsize           [100]
    http_proxy         []
    inactivity_timeout [0]
    index_expire       [1]
    inhibit_startup_message [0]
    keep_source_where  [/usr/bin/perl -MCPAN -e 'install "File::Iterator"']
    load_module_verbosity [v]
    lynx               []
    make               [/usr/bin/make]
    make_arg           []
    make_install_arg   []
    make_install_make_command [/usr/bin/make]
    makepl_arg         [INSTALLDIRS=site]
    mbuild_arg         []
    mbuild_install_arg []
    mbuild_install_build_command [./Build]
    mbuildpl_arg       []
    ncftp              []
    ncftpget           []
    no_proxy           []
    pager              [/usr/bin/less]
    password           undef
    patch              [/usr/bin/patch]
    prefer_installer   [MB]
    prefs_dir          [/usr/bin/perl -MCPAN -e 'install "XML::SemanticDiff"'/prefs]
    prerequisites_policy [ask]
    proxy_pass         undef
    proxy_user         undef
    randomize_urllist  undef
    scan_cache         [atstart]
    shell              [/bin/bash]
    show_unparsable_versions [0]
    show_upload_date   [0]
    show_zero_versions [0]
    tar                [/bin/tar]
    tar_verbosity      [v]
    term_is_latin      [1]
    term_ornaments     [1]
    test_report        [0]
    unzip              []
    urllist           
        0 [[ftp://cpan-du.viaverio.com/pub/CPAN/]](ftp://cpan-du.viaverio.com/pub/CPAN/])
        1 [[ftp://cpan-sj.viaverio.com/pub/CPAN/]](ftp://cpan-sj.viaverio.com/pub/CPAN/])
        2 [[ftp://cpan.erlbaum.net/CPAN/]](ftp://cpan.erlbaum.net/CPAN/])
        3 [[ftp://cpan.hexten.net/]](ftp://cpan.hexten.net/])
    use_sqlite         [0]
    username           undef
    wait_list          undef
    wget               [/usr/bin/wget]
    yaml_load_code     [0]
    yaml_module        [YAML]

[SIZE="5"]**Can some one suggest whats the issue here??**[/SIZE]

---

### Post by Krystanos on 2009-08-28
Hi,

Did you found an answer ? I'm having the same problem with my ubuntu server, with the same package (ubuntu-server 8.04.2)

---

