# Bài 3 — Xác thực SSH và đẩy dự án lên GitHub

**Sinh viên:** NguyễnDăngDương
**Lớp:** CNTT2
**Môn học:** IT209 — Session 04

## Tạo khóa Ed25519

```bash
ssh-keygen -t ed25519 -C "pedguedes090@outlook.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

Khóa riêng `~/.ssh/id_ed25519` không được chia sẻ hoặc đưa vào Git. Chỉ sao chép khóa công khai lên GitHub:

```bash
cat ~/.ssh/id_ed25519.pub
```

Trong GitHub, thêm nội dung `.pub` tại **Settings → SSH and GPG keys → New SSH key**. Sau đó xác minh:

```bash
ssh -T git@github.com
```

## Remote SSH và push

```bash
git remote add origin git@github.com:pedguedes090/hw03-nguyendangduong-cntt2-it209-ss4.git
git remote -v
git push -u origin main
```

Remote dùng định dạng SSH `git@github.com:OWNER/REPOSITORY.git`. `git remote -v` cần hiển thị URL này ở cả fetch và push. Không đưa private key vào báo cáo hoặc repository.
