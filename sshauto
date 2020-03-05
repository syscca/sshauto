
# Windows端下载https://git-scm.com/
# 保存脚本为sh后缀

echo -n "是否生成密钥 (y/n)? "
read keyyn
if [ "$keyyn" != "${keyyn#[Yy]}" ] ;then
	echo "正在生成密钥"
    ssh-keygen -t rsa -f ~/.ssh/id_rsa -q -N ""
else
    echo "不生成密钥"
fi

echo "输入服务器IP: "
read ipname
echo "输入SSH端口 : "
read ipprot
cat ~/.ssh/id_rsa.pub | ssh -o StrictHostKeyChecking=no root@${ipname} -p ${ipprot} "mkdir -p ~/.ssh &&\
 touch ~/.ssh/authorized_keys\
 && chmod -R go= ~/.ssh\
 && cat >> ~/.ssh/authorized_keys\
 && sed -i 's/^#\?\(PasswordAuthentication\s*\).*$/\1no/' /etc/ssh/sshd_config\
 && systemctl restart ssh"
echo "上传公钥成功并关闭密码登录，请关闭窗口"
read -n 1
