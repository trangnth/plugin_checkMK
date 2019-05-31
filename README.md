# plugin_checkMK
Check MK – Write your own check

-------------------------------
Viết plugin cho check_mk có thể được chia làm hai cách:

* Theo kiểu active check: plugin sẽ được đặt trên server, muốn sử dụng plugin cần vào dashboard để định nghĩa command cho plugin thực hiện
* Theo kiểu nrpe: Plugin sẽ được đặt trên client để check các service trên client rồi gửi kết quả về cho server (client mở port, đẩy kết quả ra đó, rồi server đọc). Với kiểu này, output của plugin cần phải tuân thủ đúng định dạng của Check_MK (không quan tâm tới code, chỉ quan tâm tới output). Có hai cách để thực hiện plugin này: một là local check, hai là plugin check. Gõ câu lệnh sau:
  
  ```sh
  [root@trang-40-71 ~(openstack)]# check_mk_agent | head
  <<<check_mk>>>
  Version: 1.5.0p16
  AgentOS: linux
  Hostname: trang-40-71
  AgentDirectory: /etc/check_mk
  DataDirectory: /var/lib/check_mk_agent
  SpoolDirectory: /var/lib/check_mk_agent/spool
  PluginsDirectory: /usr/lib/check_mk_agent/plugins
  LocalDirectory: /usr/lib/check_mk_agent/local
  ```
  
  * Nếu dùng local check thì plugin được đặt tại `/usr/lib/check_mk_agent/local`, plugin chỉ cần đặt tại client, phía server sẽ tự xử lý
  * Nếu dùng plugin check, plugin sẽ phải được viết và được đặt tại cả client lẫn server. Ưu điểm là mình có thể custom được hành động xử lý ở phía server. 
  
  Xem thêm về cách viết plugin này ở đây: https://github.com/trangnth/Monitor/tree/master/Ghichep_omd/Writing_Plugin_Check_mk 
