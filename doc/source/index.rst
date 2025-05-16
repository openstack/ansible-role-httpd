============================
OpenStack-Ansible HTTPD role
============================

This role installs an Apache Web Server for serving static files and various
applications which are required for the deployment.

To clone or view the source code for this repository, visit the role repository
for `httpd <https://opendev.org/openstack/ansible-role-httpd>`_.

Sample configuration
~~~~~~~~~~~~~~~~~~~~

.. code:: yaml

    httpd_extra_modules:
        - name: proxy
          state: present

    httpd_vhosts:
        - name: test_http
          address: "127.0.1.1"
          document_root: /var/www/test
          directories:
            - path: "/var/www/cgi-bin"
              params:
                - Options Indexes FollowSymLinks MultiViews
          headers:
            - Header set X-Content-Type-Options "nosniff"
          params:
            - Options +FollowSymLinks
          port: 80
          server_name: test_http.test_server


Default variables
~~~~~~~~~~~~~~~~~

.. literalinclude:: ../../defaults/main.yml
   :language: yaml
   :start-after: under the License.


Example playbook
~~~~~~~~~~~~~~~~

.. literalinclude:: ../../examples/playbook.yml
   :language: yaml
