---
title: "Ubuntu &amp; MySQL problems with table_cache"
date: 2008-08-19
forum: General Help
---

### Post by kempfta on 2008-08-19
I have been trying to set the table_cache variable in my my.cnf file with no luck. Currently, running a "mysqladmin variables" or "show variables" command shows:

| table_cache | 107 |

My /etc/mysql/my.cnf file has the following:

table_cache = 1024

The only thing I have found to work is logging to the database using the client and running:

mysql> set GLOBAL table_cache=1024

Then "show variables" shows the correct value of 1024 and is used properly. However, this won't survive a reboot. Really want to set this in my.cnf, for obvious reasons. Are there other variables which can cause this behavior? I have also tried setting to a lower number in case file descriptors were an issue. I couldn't event get "200" to stick.

Running this on:
mysqld Ver 5.0.51a-3ubuntu5.1-log for debian-linux-gnu on x86_64 ((Ubuntu HARDY))

Output from "show variables":
+---------------------------------+-----------------------------+
| Variable_name | Value |
+---------------------------------+-----------------------------+
| auto_increment_increment | 1 |
| auto_increment_offset | 1 |
| automatic_sp_privileges | ON |
| back_log | 50 |
| basedir | /usr/ |
| binlog_cache_size | 32768 |
| bulk_insert_buffer_size | 8388608 |
| character_set_client | latin1 |
| character_set_connection | latin1 |
| character_set_database | latin1 |
| character_set_filesystem | binary |
| character_set_results | latin1 |
| character_set_server | latin1 |
| character_set_system | utf8 |
| character_sets_dir | /usr/share/mysql/charsets/ |
| collation_connection | latin1_swedish_ci |
| collation_database | latin1_swedish_ci |
| collation_server | latin1_swedish_ci |
| completion_type | 0 |
| concurrent_insert | 1 |
| connect_timeout | 5 |
| datadir | /var/lib/mysql/ |
| date_format | %Y-%m-%d |
| datetime_format | %Y-%m-%d %H:%i:%s |
| default_week_format | 0 |
| delay_key_write | ON |
| delayed_insert_limit | 100 |
| delayed_insert_timeout | 300 |
| delayed_queue_size | 1000 |
| div_precision_increment | 4 |
| keep_files_on_create | OFF |
| engine_condition_pushdown | OFF |
| expire_logs_days | 10 |
| flush | OFF |
| flush_time | 0 |
| ft_boolean_syntax | + -><()~*:""&| |
| ft_max_word_len | 84 |
| ft_min_word_len | 3 |
| ft_query_expansion_limit | 20 |
| ft_stopword_file | (built-in) |
| group_concat_max_len | 1024 |
| have_archive | YES |
| have_bdb | NO |
| have_blackhole_engine | YES |
| have_compress | YES |
| have_crypt | YES |
| have_csv | YES |
| have_dynamic_loading | YES |
| have_example_engine | NO |
| have_federated_engine | YES |
| have_geometry | YES |
| have_innodb | DISABLED |
| have_isam | NO |
| have_merge_engine | YES |
| have_ndbcluster | DISABLED |
| have_openssl | DISABLED |
| have_ssl | DISABLED |
| have_query_cache | YES |
| have_raid | NO |
| have_rtree_keys | YES |
| have_symlink | YES |
| hostname | db1 |
| init_connect | |
| init_file | |
| init_slave | |
| innodb_additional_mem_pool_size | 1048576 |
| innodb_autoextend_increment | 8 |
| innodb_buffer_pool_awe_mem_mb | 0 |
| innodb_buffer_pool_size | 8388608 |
| innodb_checksums | ON |
| innodb_commit_concurrency | 0 |
| innodb_concurrency_tickets | 500 |
| innodb_data_file_path | |
| innodb_data_home_dir | |
| innodb_doublewrite | ON |
| innodb_fast_shutdown | 1 |
| innodb_file_io_threads | 4 |
| innodb_file_per_table | OFF |
| innodb_flush_log_at_trx_commit | 1 |
| innodb_flush_method | |
| innodb_force_recovery | 0 |
| innodb_lock_wait_timeout | 50 |
| innodb_locks_unsafe_for_binlog | OFF |
| innodb_log_arch_dir | |
| innodb_log_archive | OFF |
| innodb_log_buffer_size | 1048576 |
| innodb_log_file_size | 5242880 |
| innodb_log_files_in_group | 2 |
| innodb_log_group_home_dir | |
| innodb_max_dirty_pages_pct | 90 |
| innodb_max_purge_lag | 0 |
| innodb_mirrored_log_groups | 1 |
| innodb_open_files | 300 |
| innodb_rollback_on_timeout | OFF |
| innodb_support_xa | ON |
| innodb_sync_spin_loops | 20 |
| innodb_table_locks | ON |
| innodb_thread_concurrency | 8 |
| innodb_thread_sleep_delay | 10000 |
| interactive_timeout | 28800 |
| join_buffer_size | 131072 |
| key_buffer_size | 3221225472 |
| key_cache_age_threshold | 300 |
| key_cache_block_size | 1024 |
| key_cache_division_limit | 100 |
| language | /usr/share/mysql/english/ |
| large_files_support | ON |
| large_page_size | 0 |
| large_pages | OFF |
| lc_time_names | en_US |
| license | GPL |
| local_infile | ON |
| locked_in_memory | OFF |
| log | OFF |
| log_bin | ON |
| log_bin_trust_function_creators | OFF |
| log_error | |
| log_queries_not_using_indexes | ON |
| log_slave_updates | OFF |
| log_slow_queries | ON |
| log_warnings | 1 |
| long_query_time | 4 |
| low_priority_updates | OFF |
| lower_case_file_system | OFF |
| lower_case_table_names | 0 |
| max_allowed_packet | 16776192 |
| max_binlog_cache_size | 18446744073709551615 |
| max_binlog_size | 104857600 |
| max_connect_errors | 10 |
| max_connections | 800 |
| max_delayed_threads | 20 |
| max_error_count | 64 |
| max_heap_table_size | 524288000 |
| max_insert_delayed_threads | 20 |
| max_join_size | 18446744073709551615 |
| max_length_for_sort_data | 1024 |
| max_prepared_stmt_count | 16382 |
| max_relay_log_size | 0 |
| max_seeks_for_key | 18446744073709551615 |
| max_sort_length | 1024 |
| max_sp_recursion_depth | 0 |
| max_tmp_tables | 32 |
| max_user_connections | 800 |
| max_write_lock_count | 18446744073709551615 |
| multi_range_count | 256 |
| myisam_data_pointer_size | 6 |
| myisam_max_sort_file_size | 9223372036854775807 |
| myisam_recover_options | OFF |
| myisam_repair_threads | 1 |
| myisam_sort_buffer_size | 8388608 |
| myisam_stats_method | nulls_unequal |
| ndb_autoincrement_prefetch_sz | 32 |
| ndb_force_send | ON |
| ndb_use_exact_count | ON |
| ndb_use_transactions | ON |
| ndb_cache_check_time | 0 |
| ndb_connectstring | |
| net_buffer_length | 16384 |
| net_read_timeout | 30 |
| net_retry_count | 10 |
| net_write_timeout | 60 |
| new | OFF |
| old_passwords | OFF |
| open_files_limit | 1024 |
| optimizer_prune_level | 1 |
| optimizer_search_depth | 62 |
| pid_file | /var/run/mysqld/mysqld.pid |
| port | 3306 |
| preload_buffer_size | 32768 |
| profiling | OFF |
| profiling_history_size | 15 |
| protocol_version | 10 |
| query_alloc_block_size | 8192 |
| query_cache_limit | 8388608 |
| query_cache_min_res_unit | 4096 |
| query_cache_size | 1073741824 |
| query_cache_type | ON |
| query_cache_wlock_invalidate | OFF |
| query_prealloc_size | 8192 |
| range_alloc_block_size | 2048 |
| read_buffer_size | 131072 |
| read_only | OFF |
| read_rnd_buffer_size | 262144 |
| relay_log_purge | ON |
| relay_log_space_limit | 0 |
| rpl_recovery_rank | 0 |
| secure_auth | OFF |
| secure_file_priv | |
| server_id | 1 |
| skip_external_locking | ON |
| skip_networking | OFF |
| skip_show_database | OFF |
| slave_compressed_protocol | OFF |
| slave_load_tmpdir | /tmp/ |
| slave_net_timeout | 3600 |
| slave_skip_errors | OFF |
| slave_transaction_retries | 10 |
| slow_launch_time | 2 |
| socket | /var/run/mysqld/mysqld.sock |
| sort_buffer_size | 2097144 |
| sql_big_selects | ON |
| sql_mode | |
| sql_notes | ON |
| sql_warnings | OFF |
| ssl_ca | |
| ssl_capath | |
| ssl_cert | |
| ssl_cipher | |
| ssl_key | |
| storage_engine | MyISAM |
| sync_binlog | 0 |
| sync_frm | ON |
| system_time_zone | CDT |
| table_cache | 107 |
| table_lock_wait_timeout | 50 |
| table_type | MyISAM |
| thread_cache_size | 16 |
| thread_stack | 131072 |
| time_format | %H:%i:%s |
| time_zone | SYSTEM |
| timed_mutexes | OFF |
| tmp_table_size | 524288000 |
| tmpdir | /tmp |
| transaction_alloc_block_size | 8192 |
| transaction_prealloc_size | 4096 |
| tx_isolation | REPEATABLE-READ |
| updatable_views_with_limit | YES |
| version | 5.0.51a-3ubuntu5.1-log |
| version_comment | (Ubuntu) |
| version_compile_machine | x86_64 |
| version_compile_os | debian-linux-gnu |
| wait_timeout | 28800 |
+---------------------------------+-----------------------------+
232 rows in set (0.00 sec)[/FONT]

Thanks for ANY help you cam provide.
Todd

---

### Post by kempfta on 2008-08-19
Nevermind, I was able to solve this issue.

I misunderstood how MySQL automatically adjusts the table_cache size on startup, so it won't go over the server set file descriptor limits. I increased the number of file descriptors via /etc/security/limits.conf, and restarted mysql. ulimit -n now shows the increased number and show variables now shows tables_cache set correctly at 1024.

Consider this thread closed.

---

