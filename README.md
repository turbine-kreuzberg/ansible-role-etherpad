etherpad-lite
=============

This role will install [etherpad-lite](http://etherpad.org/) with plugins. 

Requirements
------------

By default etherpad-lite uses "Dirty.db" to store records, but it's not safe for a production environment, so you will have to use a dedicated database.
So if you set `etherpad_db_type`: "mysql" (see below), you have to include also the galaxy role `geerlingguy.mysql` and add the required parameters.
For available/required parameter see [README.md for that role](https://github.com/geerlingguy/ansible-role-mysql/).

Role Variables
--------------

| Name                                    | Default                                              | Description                                                                 |
|:----------------------------------------|:-----------------------------------------------------|:----------------------------------------------------------------------------|
| etherpad_user                           | etherpad                                             | User to create and use for etherpad-lite                                    |
| etherpad_group                          | etherpad                                             | Group to create and use for etherpad-lite                                   |
| etherpad_path_install                   | /opt/etherpad-lite                                   | Path to install etherpad-lite into                                          |
| etherpad_path_log                       | /var/log/etherpad-lite                               | Path to store etherpad-lite logs in                                         |
| etherpad_service                        | etherpad-lite                                        | Name of the etherpad-lite service (script)                                  |
| etherpad_path_initscript                | /etc/init.d/{{ etherpad_service }} **(Debian only)** | Path to service init script                                                 |
| etherpad_plugins                        | (list of default plugins see below)                  | Default plugins to install with etherpad-lite                               |
| etherpad_title                          | "Etherpad"                                           | Title for etherpad-lite installation (shown in page title)                  |
| etherpad_bind_ip                        | 0.0.0.0                                              | IP to bind etherpad-lite to                                                 |
| etherpad_bind_port                      | 9001                                                 | Port etherpad-lite listens on                                               |
| etherpad_ssl_enabled                    | false                                                | Flag to enable SSL for etherpad-lite                                        |
| etherpad_ssl_key                        | "/path-to-your/epl-server.key"                       | SSL key file                                                                |
| etherpad_ssl_cert                       | "/path-to-your/epl-server.crt"                       | SSL certificate file                                                        |
| etherpad_ssl_ca                         | - "/path-to-your/epl-intermediate-cert1.crt"         | List of SSL-CA files                                                        |
|                                         | - "/path-to-your/epl-intermediate-cert2.crt"         |                                                                             |
| etherpad_db_type                        | dirty (other possible value(s): mysql)               | Database type for storing pads (**do not use type "dirty" on production!**) |
| etherpad_db_dirty_filename              | var/dirty.db                                         | Filename for database type "dirty"                                          |
| etherpad_db_mysql_user                  | etherpad                                             | User for etherpad MySQL database                                            |
| etherpad_db_mysql_host                  | localhost                                            | Host for etherpad MySQL database                                            |
| etherpad_db_mysql_password              | mySecretPassword123                                  | Password for etherpad MySQL database                                        |
| etherpad_db_mysql_database              | etherpad                                             | Name for etherpad MySQL database                                            |
| etherpad_db_mysql_charset               | utf8mb4                                              | Charset for etherpad MySQL database                                         |
| etherpad_default_pad_text               | (too long to show here, see defaults/main.yml)       |                                                                             |
| etherpad_pad_options_no_colors          | false                                                | Config option to show no colors                                             |
| etherpad_pad_options_show_controls      | true                                                 | Config option to show controls                                              |
| etherpad_pad_options_show_chat          | true                                                 | Config option to show chat                                                  |
| etherpad_pad_options_show_line_numbers  | true                                                 | Config option to show line numbers in pad                                   |
| etherpad_pad_options_use_monospace_font | false                                                | Config option to use monospace fonts in pad                                 |
| etherpad_pad_options_user_name          | false                                                |                                                                             |
| etherpad_pad_options_user_color         | false                                                | Config option to use user colors                                            |
| etherpad_pad_options_rtl                | false                                                | Config option to display text right to left                                 |
| etherpad_pad_options_always_show_chat   | false                                                | Config option to always show chat sidebar                                   |
| etherpad_pad_options_chat_and_users     | false                                                | Config option to use chat and users                                         |
| etherpad_pad_options_lang               |                                                      | Config option to set GUI language                                           |

Dependencies
------------

None 

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: "votum.etherpad" }

License
-------

This project is under the MIT License. See the [LICENSE](LICENSE) file for the full license text.

Author Information
------------------

[Bernd Alter](https://github.com/bazoo0815) / [VOTUM GmbH](https://votum.de)
